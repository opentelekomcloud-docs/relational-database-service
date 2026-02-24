:original_name: rds_mssql_stop.html

.. _rds_mssql_stop:

Stopping a DB Instance
======================

Scenarios
---------

If you use DB instances only for routine development, you can temporarily stop instances to save money. You can stop an instance for up to 15 days.

Billing
-------

After a DB instance is stopped, the vm related to the DB instance is no longer billed. Other resources, including EIPs, storage resources, and backups, are still billed.

Constraints
-----------

-  If you stop a primary instance, read replicas (if there are any) will also be stopped. They are stopped for up to 15 days. You cannot stop a read replica without stopping the primary instance.
-  A stopped instance cannot be deleted through the console.
-  Automated backups will not be created if a DB instance is in Stopped state. After the DB instance is started, a full backup is automatically triggered.
-  If you do not manually start your stopped DB instance after 15 days, your DB instance is automatically started during the next maintenance window. For details about the maintenance window, see :ref:`Changing the Maintenance Window <rds_sqlserver_05_0038>`. To start an instance, see :ref:`Starting a DB Instance <rds_mssql_start>`.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**.
#. On the **Instances** page, locate the primary instance that you want to stop and choose **More** > **Stop** in the **Operation** column.
#. In the displayed dialog box, click **OK**.
#. Refresh the instance list and view the status of the instance. If the status is **Stopped**, the instance is stopped successfully.

.. |image1| image:: /_static/images/en-us_image_0000002388704389.png
