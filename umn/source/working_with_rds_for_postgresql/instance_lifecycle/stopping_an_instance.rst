:original_name: rds_pg_stop.html

.. _rds_pg_stop:

Stopping an Instance
====================

Scenarios
---------

If you use DB instances only for routine development, you can temporarily stop pay-per-use instances to save money. You can stop an instance for up to seven days.

Constraints
-----------

-  If you stop a primary instance, read replicas (if there are any) will also be stopped. They are stopped for up to seven days. You cannot stop a read replica without stopping the primary instance.
-  A stopped instance will not be moved to the recycle bin after being deleted.
-  If you do not manually start your stopped DB instance after seven days, your DB instance is automatically started during the next maintenance window. For details about the maintenance window, see :ref:`Changing the Maintenance Window <rds_pg_05_0038>`. To start a DB instance, see :ref:`Starting an Instance <rds_pg_start>`.
-  After a DB instance is stopped, billing for instance usage duration will stop.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the primary instance that you want to stop and choose **More** > **Stop** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the instance list and view the status of the instance. If the status is **Stopped**, the instance is stopped successfully.

.. |image1| image:: /_static/images/en-us_image_0000001420181438.png
