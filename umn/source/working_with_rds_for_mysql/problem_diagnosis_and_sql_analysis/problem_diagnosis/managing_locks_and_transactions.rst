:original_name: rds_08_0029.html

.. _rds_08_0029:

Managing Locks & Transactions
=============================

Scenarios
---------

DBA Assistant allows you to check whether your DB instance has metadata locks and InnoDB locks. You can also check the recent deadlock analysis and full deadlock analysis.

Introduction
------------

**Metadata Locks**

-  Metadata locks are used for tables to prevent conflicting DDL and DML operations from being executed concurrently on these tables. Executing DDL statements on a table generates metadata write locks. If there is a metadata lock, all subsequent SELECT, DML, and DDL operations on the table will be blocked, causing a connection backlog.
-  Metadata locks are displayed in real time. You can quickly identify problems and terminate the sessions with metadata locks to restore blocked operations.
-  DML locks are not included. You can view and analyze them on the **InnoDB Locks** page.
-  A maximum of 1,000 records can be displayed.

**InnoDB Locks**

-  InnoDB lock waits generated before DML operations are displayed in real time. You can quickly locate the session waits and any blocks that happened when multiple sessions update the same piece of data at the same time, and can terminate the source session that holds locks to restore blocked operations.
-  DDL locks, also called metadata locks, are not included. You can view and analyze them on the **Metadata Locks** page.
-  To view lock information of RDS for MySQL 8.0 instances, set **performance_schema** to **ON**. You can run the **SHOW GLOBAL VARIABLES LIKE "performance_schema"** command or refer to :ref:`Modifying Instance Parameters <rds_configuration__section360115386520>` to check the **performance_schema** settings.

**Deadlock Analysis**

-  DBA Assistant analyzes the latest deadlock log returned by **SHOW ENGINE INNODB STATUS**. If there are multiple deadlocks, only the latest one is analyzed.
-  The **innodb_deadlock_detect** parameter must be set to **ON** (only for RDS for MySQL 5.7).

**Full Deadlock Analysis**

-  DBA Assistant analyzes error logs at regular intervals, parses deadlock information, and performs comprehensive deadlock analysis.
-  Dependent parameters:

   -  The **innodb_deadlock_detect** parameter must be set to **ON** (only for RDS for MySQL 5.7).
   -  The **innodb_print_all_deadlocks** parameter must be set to **ON** and the **log_error_verbosity** parameter must be set to **3** (only for other versions than 5.7).

-  Up to 10,000 records can be displayed.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the DB instance name.
#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.
#. Click the **Locks & Transactions** tab and enter the administrator password to log in to the database.
#. On the **Locks & Transactions** tab page, perform the following operations:

   -  Click the **Metadata Locks** tab, create a lock analysis task and check whether the instance has metadata locks.

      By default, locks whose wait time is longer than 10s are displayed, but you can change this time if needed.

   -  Click the **InnoDB Locks** tab, create a lock analysis task and check whether the instance has InnoDB locks.

      By default, locks whose wait time is longer than 10s are displayed, but you can change this time if needed.

   -  Click the **Deadlock Analysis** tab and create a lock analysis task. DBA Assistant analyzes the latest deadlock log returned by **SHOW ENGINE INNODB STATUS**. If there are multiple deadlocks, only the latest one is analyzed.

      You can only query lock analysis data of the past seven days.

   -  Click the **Full Deadlock Analysis** tab and enable **Full Deadlock Analysis**. DBA Assistant regularly examines error logs, extracts deadlock details from them, and conducts a full deadlock analysis.

      You can only query lock analysis data of the past seven days.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
