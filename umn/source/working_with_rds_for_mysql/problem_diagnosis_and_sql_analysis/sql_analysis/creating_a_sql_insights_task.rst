:original_name: rds_08_0032.html

.. _rds_08_0032:

Creating a SQL Insights Task
============================

Scenarios
---------

SQL Insights allows you to not only query all executed SQL statements, but also analyze and search for the tables that are accessed and updated most frequently, and the SQL statements that have the longest lock wait, helping you quickly identify exceptions.

Constraints
-----------

-  You need to enable **Collect All SQL Statements** before using SQL Insights.

-  After **Collect All SQL Statements** is disabled, new SQL statements will not be collected anymore and the collected SQL data will be deleted.

-  If there is a buffer overrun, some data cannot be recorded.

-  Any SQL statement that exceeds 4,096 bytes will not be recorded by default.

   In RDS for MySQL 5.7.33.3 and later minor versions, you can set the **rds_sql_tracer_reserve_big_records** parameter to **ON** (which indicates that SQL statements containing more than 4,096 bytes are still recorded) on the **Parameters** page to remove this constraint. For details, see :ref:`Modifying Parameters <rds_configuration>`. RDS for MySQL 5.6 and 8.0 do not support this parameter.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the DB instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Click **SQL Explorer** and then **SQL Insights**.

#. Click |image2| next to **Collect All SQL Statements**.

   To disable this function, click **Log Settings** in the upper right corner, toggle off the **Collect All SQL Statements** switch, and click **OK**.

   .. note::

      Collecting all SQL statements generates a performance loss of no more than 5%.

#. Click **Create Task**. In the displayed dialog box, specify **Time Range**, **Dimension**, and other configuration items, and click **OK**.

#. In the task list, click **Details** in the **Operation** column to view task details.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000002390250489.png
