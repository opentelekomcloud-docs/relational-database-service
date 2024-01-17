:original_name: rds_05_0058.html

.. _rds_05_0058:

Starting a DB Instance
======================

Scenarios
---------

You can stop your DB instance temporarily to save money. After stopping your DB instance, you can restart it to begin using it again.

Constraints
-----------

-  If you start a primary DB instance, read replicas (if there are any) will also be started.
-  Only DB instances in **Stopped** state can be started. After this function is enabled, billing for instance usage duration will start.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the primary DB instance that you want to start and choose **More** > **Start** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the DB instance list and view the status of the DB instance. If the status is **Available**, the DB instance is started successfully.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
