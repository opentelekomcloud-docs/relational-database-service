:original_name: rds_09_0065.html

.. _rds_09_0065:

rds_pg_sql_ccl
==============

Introduction
------------

To prevent highly concurrent SQL statements that consume too many resources from causing instance instability, RDS for PostgreSQL provides rds_pg_sql_ccl, ccl is short for concurrent control. SQL statement concurrency control can ensure instance stability, optimize performance, and guarantee resources for critical tasks in the following scenarios:

-  When workloads increase sharply, the instance stability is ensured by limiting the execution of a certain type of SQL statements.
-  When there are not enough resources, the success of core tasks is ensured by limiting the execution of other SQL statements to reduce resource consumption.

This extension provides two concurrency control methods:

-  Method 1: It limits the number of SQL statements that can be executed at the same time. This number is specified by the **rds_pg_sql_ccl.max_concurrent_sql** parameter. The default value is **-1**, indicating that the number is not limited.
-  Method 2: It limits the number of a certain type of SQL statements (with the same query ID) that can be executed at the same time. This number is specified by concurrency control rules. For details about concurrency control rules, see below.

Supported Versions
------------------

This extension is available to the latest minor versions of RDS for PostgreSQL 11.20, 12.15, 13.11, 14.8, 15.4, 16.2, and above. You can run the following SQL statement to check whether your DB instance supports this extension:

.. code-block::

   SELECT * FROM pg_available_extension_versions WHERE name = 'rds_pg_sql_ccl';

If this extension is not supported, :ref:`upgrade the minor version of your DB instance <rds_pg_05_0003>`.

To see more extensions supported by RDS for PostgreSQL, go to :ref:`Supported Plugins <rds_09_0045>`.

Notes
-----

SQL statement concurrency control rules must be configured based on workloads and resource usage.

Creating Rules
--------------

#. In any given database, each rule must have a unique query ID, but rules in different databases can have the same query ID.
#. A rule does not take effect immediately after being created. You need to call the **enable_ccl_rule** function to make it applied.
#. The **get_query_id** function cannot obtain the query IDs of SQL statements using bind variables, and the **add_ccl_rule_by_query** function cannot limit the execution of such SQL statements.
#. You can obtain the query ID of a SQL statement with bind variables using the pg_stat_statements extension. Then, you can use **add_ccl_rule_by_queryid** to create rules. For details, see "Concurrency Control for SQL Statements with Bind Variables".

How Rules Take Effect
---------------------

#. Method 1 limits the number of SQL statements that can be concurrently executed. Rules creating using this method take effect preferentially. On the basis of method 1, you can use method 2 to further limit concurrent execution of a specific type of SQL statements.
#. After an instance reboot, none of the rules are applied.
#. Read replicas synchronize the rules of the primary instance and call the **enable_ccl_rule** function to make the rules apply.
#. A rule is only applied to SQL statements executed after the rule was enabled.

Concurrency Control for SQL Statements Without Bind Variables
-------------------------------------------------------------

Prerequisites:

#. Install the kernel extension rds_pg_sql_ccl on the console or by running SQL statements.

   .. code-block::

      SELECT control_extension ('create', 'rds_pg_sql_ccl');

#. Set kernel parameters.

   .. code-block::

      rds_pg_sql_ccl.enable_ccl = on

Then, perform the following operations:

#. On the **Instances** page, click the instance name to go to the **Overview** page.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Choose **SQL Explorer** > **Concurrency Control**.
#. Toggle on the concurrency control switch.
#. Click **Add Rule** and configure required parameters.

   -  Locate the rule and click **Enable** in the **Operation** column to enable the rule.
   -  To disable a rule, click **Disable**.
   -  To delete a rule, click **Delete**. After a concurrency control rule that is enabled is deleted, the rule is not applied anymore.

Concurrency Control for SQL Statements with Bind Variables
----------------------------------------------------------

Drivers such as JDBC support prepared statements. They precompile parameterized SQL statements and execute them after parameters are entered. In the pg_stat_statements view, the statements are displayed as bind variables. For SQL statements using bind variables, the query IDs calculated by the kernel are different from those of the same statements using actual parameter values. The concurrent execution of such statements cannot be limited by adding the statements.

Such SQL statements can only be limited by executing them first and then adding concurrency control rules.

#. Execute a SQL statement with bind variables. In this way, the kernel calculates its query ID. An example of the JDBC-based prepared statement program is as follows:

   .. code-block::

      String sql = "select pg_sleep(?);";
      PreparedStatement preparedStatement = conn.prepareStatement(sql);
      preparedStatement.setInt(1, 500);
      ResultSet resultSet = preparedStatement.executeQuery();

#. Query the query ID of the SQL statement in the pg_stat_statements view.

   .. code-block::

      select queryid from pg_stat_statements where query ilike '%SELECT pg_sleep%';

#. Add a concurrency control rule based on the query ID.

   .. code-block::

      select rds_pg_sql_ccl.add_ccl_rule_by_queryid($queryid);

#. Enable the rule based on the return value (**rule_id**) of the previous SQL statement.

   .. code-block::

      select rds_pg_sql_ccl.enable_ccl_rule($rule_id);

#. Obtain all rules applied from the get_all_enabled_rule view provided by the extension.

   .. code-block::

      select * from rds_pg_sql_ccl.get_all_enabled_rule;

Parameters
----------

.. table:: **Table 1** Parameter description

   +-----------------------------------+-----------+---------------+---------------+---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Data Type | Default Value | Maximum Value | Minimum Value | Description                                                                                                                                                                                               |
   +===================================+===========+===============+===============+===============+===========================================================================================================================================================================================================+
   | rds_pg_sql_ccl.enable_ccl         | bool      | false         | ``-``         | ``-``         | Whether to enable a concurrency control rule.                                                                                                                                                             |
   +-----------------------------------+-----------+---------------+---------------+---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rds_pg_sql_ccl.max_enabled_rules  | int       | 5000          | 500000        | 0             | The number of rules that take effect at the same time.                                                                                                                                                    |
   +-----------------------------------+-----------+---------------+---------------+---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rds_pg_sql_ccl.max_concurrent_sql | int       | -1            | 50000         | -1            | The number of SQL statements that can be concurrently executed (its priority is higher than that of concurrency control rules). If the value is less than 0, the number of SQL statements is not limited. |
   +-----------------------------------+-----------+---------------+---------------+---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Function Interface Description
------------------------------

.. table:: **Table 2** Function interface description

   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+
   | No.         | Function                               | Parameter                         | Return Value | Description                                               |
   +=============+========================================+===================================+==============+===========================================================+
   | 1           | rds_pg_sql_ccl.get_query_id            | query_string text,                | queryid      | Calculates the query ID of a SQL statement.               |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | search_path text default 'public' |              |                                                           |
   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+
   | 2           | rds_pg_sql_ccl.add_ccl_rule_by_query   | query_string text,                | ruleid       | Adds a concurrency control rule using SQL statements.     |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | max_concurrency int default 0,    |              |                                                           |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | max_waiting int default 0,        |              |                                                           |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | search_path text default 'public' |              |                                                           |
   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+
   | 3           | rds_pg_sql_ccl.add_ccl_rule_by_queryid | query_id bigint,                  | ruleid       | Adds a concurrency control rule based on the query ID.    |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | max_concurrency int default 0,    |              |                                                           |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | max_waiting int default 0,        |              |                                                           |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | search_path text default 'public' |              |                                                           |
   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+
   | 5           | rds_pg_sql_ccl.enable_ccl_rule         | rule_id bigint                    | bool         | Enables a concurrency control rule based on the rule ID.  |
   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+
   | 6           | rds_pg_sql_ccl.disable_ccl_rule        | rule_id bigint                    | bool         | Disables a concurrency control rule based on the rule ID. |
   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+
   | 7           | rds_pg_sql_ccl.disable_all_ccl_rule    | ``-``                             | void         | Disables all rules.                                       |
   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+
   | 8           | rds_pg_sql_ccl.delete_ccl_rule         | rule_id bigint                    | void         | Deletes a concurrency control rule based on the rule ID.  |
   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+
   | 9           | rds_pg_sql_ccl.update_ccl_rule         | new_rule_id bigint,               | void         | Updates a concurrency control rule based on the rule ID.  |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | new_max_concurrency int,          |              |                                                           |
   |             |                                        |                                   |              |                                                           |
   |             |                                        | new_max_waiting int               |              |                                                           |
   +-------------+----------------------------------------+-----------------------------------+--------------+-----------------------------------------------------------+

Description of some parameters:

-  **max_concurrency**: The maximum number of SQL statements that can be concurrently executed.
-  **max_wait**: The maximum waiting time after which new SQL statements of a specified type will fail to be executed when the maximum number of concurrent SQL statements is reached.
-  **new_max_concurrency**: The new maximum number of concurrent SQL statements.
-  **new_max_wait**: The new maximum waiting time.

View Interface Description
--------------------------

.. table:: **Table 3** View interface description

   +-----------------+------------------------------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | No.             | View                                     | Column                       | Description                                                                                                                       |
   +=================+==========================================+==============================+===================================================================================================================================+
   | 1               | rds_pg_sql_ccl.get_all_enabled_rule      | dbid oid,                    | Displays all concurrency control rules applied.                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | queryid bigint,              |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | max_concurrency int,         |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | max_wait int                 |                                                                                                                                   |
   +-----------------+------------------------------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | 2               | rds_pg_sql_ccl.get_activity_query_status | queryid bigint,              | Displays the status of each SQL statement in the current instance, such as the query ID and whether the SQL statement is waiting. |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | wait_start_time timestamptz, |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | pid int,                     |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | dbid oid                     |                                                                                                                                   |
   +-----------------+------------------------------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | 3               | rds_pg_sql_ccl.get_current_db_ccl_rule   | rule_id bigint,              | Displays the concurrency control rules created for the current database (whether applied or not).                                 |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | query_id bigint,             |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | query_string,                |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | max_concurrency int,         |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | max_waiting int,             |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | search_path text,            |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | create_time timestamptz,     |                                                                                                                                   |
   |                 |                                          |                              |                                                                                                                                   |
   |                 |                                          | enabled bool                 |                                                                                                                                   |
   +-----------------+------------------------------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
