:original_name: rds_06_0003.html

.. _rds_06_0003:

Viewing Monitoring Metrics
==========================

Scenarios
---------

Cloud Eye monitors the statuses of RDS DB instances. You can view RDS monitoring metrics on the management console.

Monitored data takes some time before it can be displayed. The RDS status displayed on the Cloud Eye console is about 5 to 10 minutes delayed. When you create a new RDS DB instance, it takes 5 to 10 minutes before monitoring data is displayed on Cloud Eye.

Prerequisites
-------------

-  RDS is running properly.

   Monitoring metrics of the RDS DB instances that are faulty or have been deleted are not displayed on the Cloud Eye console. You can view their monitoring metrics after they are rebooted or restored to normal.

.. note::

   If an RDS DB instance has been faulty for 24 hours, Cloud Eye considers it to no longer exist and deletes it from the monitoring object list. You need to manually clear the alarm rules created for the DB instance.

-  RDS has been running properly for about 10 minutes.

   For a newly created RDS DB instance, you need to wait a bit before you can view the metrics.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and click **View Metrics** in the **Operation** column to go to the Cloud Eye console.

   Alternatively, click the target DB instance. On the displayed page, click **View Metrics** in the upper right corner of the page to go to the Cloud Eye console.

#. On the Cloud Eye console, view monitoring metrics of the primary DB instance.

   Cloud Eye can monitor performance metrics from the last 1 hour, 3 hours, 12 hours, 1 day, 30 days, and 7 days.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
