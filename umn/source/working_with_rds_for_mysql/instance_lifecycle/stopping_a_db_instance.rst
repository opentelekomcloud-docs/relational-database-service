:original_name: rds_05_0057.html

.. _rds_05_0057:

Stopping a DB Instance
======================

Scenarios
---------

If you use DB instances only for routine development, you can temporarily stop pay-per-use DB instances to save money. You can stop a DB instance for up to seven days.

Constraints
-----------

-  If you stop a primary DB instance, read replicas (if there are any) will also be stopped. They are stopped for up to seven days. You cannot stop a read replica without stopping the primary DB instance.
-  A stopped DB instance will not be moved to the recycle bin after being deleted.
-  If you do not manually start your stopped DB instance after seven days, your DB instance is automatically started during the next maintenance window. For details about the maintenance window, see :ref:`Changing the Maintenance Window <rds_05_0038>`. To start a DB instance, see :ref:`Starting a DB Instance <rds_05_0058>`.
-  After a DB instance is stopped, billing for instance usage duration will stop.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the primary DB instance that you want to stop and choose **More** > **Stop** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the DB instance list and view the status of the DB instance. If the status is **Stopped**, the DB instance is stopped successfully.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
