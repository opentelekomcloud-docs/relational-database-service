:original_name: rds_pg_10_0001.html

.. _rds_pg_10_0001:

Suggestions on PostgreSQL Parameter Tuning
==========================================

Parameters are key configuration items in a database system. Improper parameter settings may adversely affect the stable running of databases. This section describes some important parameters for your reference. For details, visit the `PostgreSQL official website <https://www.postgresql.org/docs/current/runtime-config.html>`__.

For details on how to modify PostgreSQL parameters on the console, see :ref:`Modifying Instance Parameters <rds_pg_configuration>`.

Sensitive Parameters
--------------------

The following parameters can result in system security and stability issues if set improperly:

-  The **search_path** parameter must be set to a schema sequence where schemas are separated by commas (,). Ensure that the schemas exist. Otherwise, the database performance will be affected.
-  If you enable the parameter **log_duration**, SQL statements containing sensitive information may be recorded in logs. You are advised to disable this parameter.
-  **log_min_duration_statement** specifies how many milliseconds a query has to run before it has to be logged. The unit is millisecond. Setting this parameter to **0** means that all statements are recorded. Setting this parameter to **-1** means that no statement is recorded. For details, see :ref:`Viewing Slow Query Logs <slow_query_log-pg>`.
-  The parameters **nls_timestamp_format** and **nls_date_format** control the input and output formats of timestamp and date. They are available only for PostgreSQL Enhanced Edition.

   -  The **nls_timestamp_format** parameter defines the timestamp format. The **nls_date_format** defines the date format.

-  The **temp_file_limit** parameter specifies the maximum amount of disk space (in KB) that a session can use for temporary files. It supports PostgreSQL 11, 12, and 13 only. Changing this parameter value is a high-risk operation. Exercise caution when deciding to perform this operation.

   -  If the parameter value exceeds the threshold, the DB instance will become unavailable.
   -  If the parameter value is changed to a larger value for temporary use but is not changed to the original value after the use, the disk space will be continuously used to store temporary files. If the disk space is used up, services will be interrupted and the DB instance will become unavailable.

Performance Parameters
----------------------

The following parameters can affect database performance:

-  If **log_statement** is set to **ddl**, **mod**, or **all**, the operations for creating and deleting database users (including passwords and other sensitive information) are recorded. This operation affects database performance. Exercise caution when setting this parameter.
-  Enabling the following parameters will affect the database performance: **log_hostname**, **log_duration**, **log_connections**, and **log_disconnections**. Exercise caution when enabling these parameters.
