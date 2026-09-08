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
#. In the navigation pane, choose **SQL Analysis and Tuning** under **DBA Assistant**.
#. Click the **Slow Query Logs** tab.

   .. note::

      Slow SQL Analysis needs to be purchased separately. To use this function, upgrade DBA Assistant first.

#. Click **Upgrade DBA Assistant**. In the displayed dialog box, you can learn about the enhanced features and billing rules.
#. View slow queries over time and archived slow query logs in the last 1 hour, last 3 hours, last 12 hours, or a custom time period (spanning no more than one day).
#. To export slow query log details or statistics, click the **Details** or **Statistics** tab above the log list and click **Export** on the tab page.

Follow-up Operations
--------------------

To view historical export records, do as follows:

#. Above the log list, click the **Details** or **Statistics** tab.
#. Click **View All Export Records**. The displayed dialog box shows all historical export records.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
