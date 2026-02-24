:original_name: rds_pg_08_0027.html

.. _rds_pg_08_0027:

Viewing Performance Metrics of a DB Instance
============================================

Scenarios
---------

DBA Assistant allows you to view the performance metrics of your DB instance. Historical trends of performance metrics within a specified time period help you learn about the status and resource usage of your DB instance. If any alarm is reported, you can take actions timely.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target instance name.
#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.
#. Click the **Performance** tab. You can perform the following operations on this tab page:

   -  Click **View Details** to view metric changes of your instance in the same period on different days.

      To view more metrics, see :ref:`Viewing Monitoring Metrics <rds_pg_06_0003>`.

   -  Click **Create Alarm Rule** to go to the Cloud Eye console and customize alarm rules and notification policies. By this way, you can learn about your instance status in a timely manner.

      For details, see :ref:`Setting Alarm Rules <rds_pg_06_0002>`.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
