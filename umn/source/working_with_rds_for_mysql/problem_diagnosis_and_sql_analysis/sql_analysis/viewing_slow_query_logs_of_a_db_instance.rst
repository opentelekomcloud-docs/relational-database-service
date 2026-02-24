:original_name: rds_08_0030.html

.. _rds_08_0030:

Viewing Slow Query Logs of a DB Instance
========================================

Scenarios
---------

**Slow Query Log** displays a chart of SQL statements that are taking too long to execute and allows you to sort slow SQL statements by multiple dimensions, such as by user, host, or SQL template. It helps you quickly identify bottlenecks and improve instance performance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the DB instance name.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Click the **Slow Query Logs** tab.

   .. note::

      Slow SQL Analysis needs to be purchased separately. To use this function, subscribe to Intelligent O&M first.

#. Click **Subscribe**. In the displayed dialog box, you can learn about Intelligent O&M functions and pricing.
#. After subscribing to Intelligent O&M, view slow queries over time of your instance.
#. You can view slow queries over time and you can see the slow log archive history for the last 1 hour, last 3 hours, last 12 hours, or a custom time period (spanning no more than one day).
#. View slow query log details and template statistics.

   -  To export slow query log information, click **Export**.
   -  To view log export history, click **View Export List**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
