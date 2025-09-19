:original_name: rds_mssql_start.html

.. _rds_mssql_start:

Starting a DB Instance
======================

Scenarios
---------

You can stop your instance temporarily to save money. After stopping your instance, you can restart it to begin using it again.

Billing
-------

After a DB instance is started, the VM where the DB instance is located is billed again.

Constraints
-----------

-  If you start a primary instance, read replicas (if there are any) will also be started.
-  When a stopped DB instance is started, a full backup is automatically triggered.
-  Only instances in **Stopped** state can be started.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**.
#. On the **Instances** page, locate the primary instance that you want to start and choose **More** > **Start** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the instance list and view the status of the instance. If the status is **Available**, the instance is started successfully.

.. |image1| image:: /_static/images/en-us_image_0000002378606722.png
