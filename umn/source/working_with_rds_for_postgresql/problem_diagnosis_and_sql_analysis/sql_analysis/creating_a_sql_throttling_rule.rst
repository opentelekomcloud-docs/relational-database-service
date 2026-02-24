:original_name: rds_pg_08_0033.html

.. _rds_pg_08_0033:

Creating a SQL Throttling Rule
==============================

Scenarios
---------

You can create rules to control concurrent execution of SQL statements by specifying original SQL statements or query ID. When the number of matched SQL statements exceeds the maximum number of concurrent SQL statements allowed, the DB instance rejects the SQL statements to ensure stability.

It can be used in the following scenarios:

-  When workloads increase sharply, the instance stability is ensured by limiting the execution of a certain type of SQL statements.
-  When there are not enough resources, the success of core tasks is ensured by limiting the execution of other SQL statements to reduce resource consumption.

Supported Versions
------------------

SQL throttling is available in the following versions:

-  RDS for PostgreSQL 17
-  RDS for PostgreSQL 16
-  RDS for PostgreSQL 15: 15.4 and later
-  RDS for PostgreSQL 14: 14.8 and later
-  RDS for PostgreSQL 13: 13.11 and later
-  RDS for PostgreSQL 12: 12.15 and later
-  RDS for PostgreSQL 11: 11.20 and later

Constraints
-----------

-  SQL statements executed by built-in users (rdsAdmin, rdsMetric, rdsRepl, and rdsBackup) are not affected by SQL throttling rules.
-  To use SQL throttling, the rds_pg_sql_ccl extension must be installed. For details, see :ref:`Installing and Uninstalling a Plugin on the RDS Console <rds_09_0070>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Choose **SQL Explorer** > **SQL Throttling**.

#. Toggle on the SQL throttling switch |image2|.

   .. note::

      SQL throttling rules take effect only after SQL throttling is enabled.

#. Click **Add Rule**. Configure the parameters listed in :ref:`Table 1 <rds_pg_08_0033__table8389114111240>`.

   .. note::

      Configure SQL throttling rules based on workloads and resource usage.

   .. _rds_pg_08_0033__table8389114111240:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                  |
      +===================================+==============================================================================================================================================+
      | Mode                              | -  Original SQL Statements                                                                                                                   |
      |                                   |                                                                                                                                              |
      |                                   |    A rule created using SQL statements cannot be applied to SQL statements with bind variables.                                              |
      |                                   |                                                                                                                                              |
      |                                   | -  Query ID                                                                                                                                  |
      |                                   |                                                                                                                                              |
      |                                   |    In any given database, each rule must have a unique query ID, but rules in different databases can have the same query ID.                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Concurrency                  | The maximum allowed number of concurrent SQL statements that match the rule. SQL statements exceeding this upper limit will not be executed. |
      |                                   |                                                                                                                                              |
      |                                   | The value ranges from 0 to 50000. **0** indicates that the concurrency of SQL statements is not limited.                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Wait Time                    | Wait time before the SQL statements can be executed. The value ranges from 0ms to 1000000000ms.                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm the settings and click **OK**.

#. A rule is not applied immediately after being created. To apply the rule, click **Enable**.

Follow-up Operations
--------------------

If a SQL throttling rule is not required, you can disable or delete it in the **Operation** column.

-  To disable a rule, click **Disable**.
-  To delete a rule, click **Delete**. After a SQL throttling rule that is enabled is deleted, the rule is not applied anymore.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000002390330397.png
