:original_name: rds_11_0006.html

.. _rds_11_0006:

Rebooting DB Instances or Read Replicas
=======================================

**Scenarios**
-------------

You may need to reboot a DB instance during maintenance. For example, after modifying some parameters, a reboot is required for the modifications to take effect. You can reboot a primary DB instance or a read replica on the management console.

Constraints
-----------

-  If the database service status is abnormal, you can forcibly reboot the DB instance, but this will interrupt uncommitted transactions.
-  Rebooting DB instances will cause service interruptions. During the reboot process, the DB instance status is **Rebooting**.
-  Rebooting DB instances will cause instance unavailability and clear cached memory. To prevent traffic congestion during peak hours, you are advised to reboot DB instances during off-peak hours.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance, or click |image2| and then locate the target read replica. Choose **More** > **Reboot** in the **Operation** column.

   Alternatively, click the target DB instance on the **Instances** page to go to the **Basic Information** page. In the upper right corner, click **Reboot**.

   For primary/standby DB instances, if you reboot the primary DB instance, the standby DB instance is also rebooted automatically.

#. In the displayed dialog box, select a reboot mode. If you select **Forceful**, select the checkbox before **Confirm forcible reboot** and click **Yes**.

#. Refresh the DB instance list and view the status of the DB instance. If its status is **Available**, it has rebooted successfully.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001145211620.png
