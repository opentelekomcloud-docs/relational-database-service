:original_name: rds_pg_08_0025.html

.. _rds_pg_08_0025:

Introduction to Instance Overview
=================================

On the **Overview** page, you can get knowledge of the overall status of your RDS for PostgreSQL instance, including alarms, intelligent anomaly diagnosis, and key performance metrics. DBA Assistant diagnoses instance health using operational data analytics and intelligent algorithms, and provides you with solutions and suggestions for handling detected exceptions.

Functions
---------

:ref:`Table 1 <rds_pg_08_0025__table29401349134416>` lists the functions provided on the **Overview** page.

.. _rds_pg_08_0025__table29401349134416:

.. table:: **Table 1** Function description

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                          | Description                                                                                                                                                                       |
   +===================================+===================================================================================================================================================================================+
   | Instance Information              | Shows basic information about your instance and allows you to modify the instance.                                                                                                |
   |                                   |                                                                                                                                                                                   |
   |                                   | -  Basic Information                                                                                                                                                              |
   |                                   |                                                                                                                                                                                   |
   |                                   |    This area displays the DB instance name/ID, description, AZ, and enterprise project, and allows you to configure a maintenance window, configure SSL, and reset root password. |
   |                                   |                                                                                                                                                                                   |
   |                                   | -  Configurations                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                   |
   |                                   |    This area displays the DB engine version, and allows you to switch between the primary and standby nodes, change the instance class, scale up storage.                         |
   |                                   |                                                                                                                                                                                   |
   |                                   | -  Connectivity                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                   |
   |                                   |    This area displays the VPC and subnet, and allows you to change the floating IP address, change the database port, and manage security groups.                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Alarms                            | To view alarm details, click the number next to an alarm severity.                                                                                                                |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Intelligent Anomaly Diagnosis     | Shows the health status of your instance based on operational data analytics and intelligent algorithms.                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Performance Monitoring            | Shows key performance metrics of the instance, including the CPU usage, memory usage, number of SQL statements executed for more than 3s, and connections.                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Storage & Backup                  | Shows the storage space and backup space usage of your instance, and allows you to scale up the storage.                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Instance Information
--------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target instance name to go to the **Overview** page.
#. In the **Instance Information** area, check the instance information and modify the instance as required.

Alarms
------

In the **Alarms** area, check alarm information of your instance.

Based on the configured alarm rules, you can see active alarms of your instance, including alarms in the **Alarm** (metric) or **Triggered** (event) state.

-  To check all alarm records, click **All Alarms**.

-  To configure alarm rules, click **Alarm Settings**.

-  To check alarms over time, select a time window in the upper part of the **Alarms** area.

   The time window can be last 1 hour, last 6 hours, last 12 hours, last 24 hours, last 7 days, last 30 days, or a custom time period.

Intelligent Anomaly Diagnosis
-----------------------------

In the **Intelligent Anomaly Diagnosis** area, view the health diagnosis results of your instance.

Intelligent Anomaly Diagnosis provides diagnosis results for the check items in the past 5 minutes. If any diagnosis result is abnormal, the check item is abnormal in the past 5 minutes.

Performance Monitoring
----------------------

In the **Performance Monitoring** area, you can view the vCPUs (used/total), memory (used/total), number of SQL statements executed for more than 3s, and connections of your instance.

-  To check all metrics, click **Real-Time Monitoring** to go to the DBA Assistant page. For details, see :ref:`Viewing Performance Metrics of a DB Instance <rds_pg_08_0027>`.

-  To check the analysis results of slow queries, click **Slow SQL Log** to go to the DBA Assistant page. For details, see :ref:`Viewing Slow Query Logs of a DB Instance <rds_pg_08_0030>`.

-  To check metric changes over time, select a time range in the upper part.

   The time window can be last 1 hour, last 6 hours, last 12 hours, last 24 hours, last 7 days, last 30 days, or a custom time period.

Storage & Backup
----------------

In the **Storage & Backup** area, you can check the storage space usage and backup space usage of your instance, enable disk encryption, and scale up storage space.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
