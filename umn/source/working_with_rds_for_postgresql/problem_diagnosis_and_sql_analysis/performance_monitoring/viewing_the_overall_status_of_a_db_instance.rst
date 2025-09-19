:original_name: rds_pg_08_0025.html

.. _rds_pg_08_0025:

Viewing the Overall Status of a DB Instance
===========================================

On the **Dashboard** page, you can get knowledge of the overall status of your instance, including alarms, resource usages, and key performance metrics. DBA Assistant diagnoses instance health using operational data analytics and intelligent algorithms, and provides you with solutions and suggestions for handling detected exceptions.

Functions
---------

:ref:`Table 1 <rds_pg_08_0025__table29401349134416>` lists the functions provided by Dashboard.

.. _rds_pg_08_0025__table29401349134416:

.. table:: **Table 1** Function description

   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Function                | Description                                                                                                                         |
   +=========================+=====================================================================================================================================+
   | Alarms                  | To view alarm details, click the number next to an alarm severity.                                                                  |
   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Health                  | Shows the health status of your instance based on operational data analytics and intelligent algorithms.                            |
   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Resources               | Shows the vCPU usage, memory usage, storage usage, and disk IOPS of your instance.                                                  |
   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Key Performance Metrics | Shows vCPU utilization & slow query logs, connections, memory utilization, and disk reads/writes of your instance in the last hour. |
   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------+

Alarms
------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the DB instance name.
#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.
#. On the **Dashboard** page, view the status of your instance.

   -  In the **Alarms** area, view alarm information of your instance.

      You can customize alarm rules by adjusting alarm policies and severities for key metrics, such as CPU usage and disk usage. To view alarm details, click the number next to an alarm severity.

   -  In the **Health** area, view the health diagnosis results of your instance.

   -  In the **Resources** area, view the resource usages of your instance.

   -  In the **Key Performance Metrics** area, view the key performance metrics of your instance in the last hour.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
