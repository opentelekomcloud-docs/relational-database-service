:original_name: rds_mssql_10_0000.html

.. _rds_mssql_10_0000:

Suggestions on Using RDS for SQL Server
=======================================

**Instance Class**
------------------

Do not use instances with 2 vCPUs and 4 GB memory for production workloads. Such instances are provided only for experience testing.

Use instances with at least 4 vCPUs and 8 GB memory for production workloads. Instances with 2 vCPUs and 4 GB memory are not suitable for production workloads because Microsoft SQL Server runs on Windows and both the engine and the OS require a large number of resources. Using instances with 2 vCPUs and 4 GB memory for a long time may result in memory exhaustion and system freezing.

**Database Connection**
-----------------------

-  Use the form of "ip,port" (use a comma (,) between them) to connect to an RDS for SQL Server instance.
-  Do not use the server name to connect to a database.
-  Your application must be able to reconnect to the database if a disaster occurs in the database or the database is disconnected.

**Database Migration**
----------------------

After the migration is complete, perform the following operations:

-  Check the permissions integrity. Database migration only restores data. Other service-level permissions, such as those for database users and login names, must be recreated and re-associated with database accounts.
-  Recreate indexes. After the migration is complete, the physical environment of data files changes, and the database indexes become invalid. You need to recreate the indexes to minimize the impact on the database performance.
-  Compare parameter settings. After data is migrated to the cloud, RDS for SQL Server uses parameter groups provided on the cloud. You need to compare the parameter settings on the cloud with those of the original on-premises database. Modify the parameter settings on the cloud to keep them the same as those for the original database.

**Instance Usage**
------------------

-  Although RDS for SQL Server supports it, creating an instance configured with the AD domain is not recommended. This is because the domain controller server is deployed on the user side, and the user has overly lax permissions. If the user changes the group policy configurations of the domain controller server, the DB instance security can be affected.
-  There can be no more than 100 databases in a single instance. The maximum number of databases that a single DB instance supports depends on the instance specifications. Too many databases occupy resources such as worker threads, which impacts instance performance.
-  Do not use the sysadmin role to connect your application to a database. An account with the sysadmin role has the super administrator permission. Improper use of this account will threaten database security and stability. RDS does not grant the super administrator permission to any user.
-  Do not create tables in the system database. Create a user-defined database to store user data. Do not create any tables in the system database to write data because storing data in the system database is insecure.
-  Do not enable the AutoClose property for the database. Enabling AutoClose may result in failures to establish the replication relationship between primary and standby DB instances.
-  Do not set the database to single-user mode. Single-user mode allows only one session to access the database at a time. If a fault occurs in the database, sessions initiated by O&M personnel will be unable to connect to the database. If you have set your database to single-user mode, change it to multi-user mode.
-  Do not leave **Slow Query Log** enabled for a long time. Slow query logs help analyze slow SQL statements. However, if **Slow Query Log** is enabled for a long time, database performance will deteriorate. You are advised to disable **Slow Query Log** when you are not tracing or analyzing SQL problems.
-  Schedule a time to automatically recreate indexes. When a database is used for a long time, a large number of index fragments may be generated. This slows down database access. To address this issue, create an SQL Agent job to recreate indexes once a month.
-  Update statistics periodically. Database statistics need to be updated at regular intervals. You are advised to create an SQL Agent job to update statistics once a week.
-  Pay attention to the database size and shrink the database as required. If a database has been used for a long time, some physical space may not be released in a timely manner. In this case, you need to shrink the database to release the physical space. Pay attention to the log file size and physical file size. If any file bloat is found, shrink the database during off-peak hours.
-  The database name cannot exceed 64 characters. Only digits, uppercase letters, lowercase letters, hyphens (-), and underscores (_) are allowed.
-  You are advised to change the default port. The default port of RDS for SQL Server is **1433**. Some insecure programs on the Internet may scan the default port.
-  You are advised to use primary/standby instances. Primary/standby instances provide much better availability and reliability for production workloads.
-  Deploy primary/standby instances across AZs for AZ-level DR.
-  During off-peak hours, reboot instances that have been running for a long time. When an instance has been running for a long time, its performance may deteriorate. You are advised to reboot the instance every three months during off-peak hours.
-  Configure the maximum degree of parallelism. This parameter affects the CPU usage of your workloads. Its default value is **0**, indicating that a session can use all CPUs. If you set it to the default value, the CPUs may not be allocated to other sessions due to a SQL problem. You are advised to configure this parameter based on instance specifications, for example, setting it to the value of the number of cores divided by 2.
-  Create multiple NDF files for the tempdb database.
-  If there is a permissions problem when you perform an operation, refer to :ref:`Usage of Stored Procedures <rds_09_0001>` to find a proper stored procedure.
-  To modify SQL Server parameters, instead of running SQL commands, modify them on the console.
-  Back up and restore data on the console or by calling RDS APIs or SDK APIs. Do not use SQL Server Management Studio (SSMS) or SQL statements for backup and restoration.
-  Restoring data to an existing DB instance may cause existing data to be overwritten. Exercise caution when performing this operation. You are advised to restore data to a new DB instance.
-  Set the recovery model of your database to FULL instead of SIMPLE.

   -  In the SIMPLE recovery model, no incremental backup is performed for the database, so the database cannot be restored to a specified time point.
   -  For primary/standby or cluster instances, if the recovery model is set to SIMPLE, no replication relationship will be established for the instances. As a result, a primary/standby switchover or instance class change cannot be performed.
