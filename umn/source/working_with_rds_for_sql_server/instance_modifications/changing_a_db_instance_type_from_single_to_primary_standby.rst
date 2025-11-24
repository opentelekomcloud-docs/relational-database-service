:original_name: rds_sqlserver_05_0023.html

.. _rds_sqlserver_05_0023:

Changing a DB Instance Type from Single to Primary/Standby
==========================================================

Scenarios
---------

-  RDS enables you to change single DB instances to primary/standby DB instances to improve instance reliability.
-  Primary/standby DB instances support automatic failover. If the primary DB instance fails, the standby DB instance takes over services quickly. You are advised to deploy primary and standby DB instances in different AZs for high availability and disaster recovery.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate a single DB instance and choose **More** > **Change Type to Primary/Standby** in the **Operation** column.
#. Select a standby AZ and enter the original administrator password. Other configurations are the same as those of the primary DB instance by default. Confirm the configurations and click **Submit**.
#. After a single DB instance is changed to primary/standby instance, you can view and manage it on the **Instances** page.

   -  The DB instance is in the **Changing type to primary/standby** status. You can view the progress on the **Task Center** page. For details, see :ref:`Task Center <rds_sqlserver_05_0007>`.
   -  In the upper right corner of the DB instance list, click |image2| to refresh the list. After the DB instance type is changed to primary/standby, the instance status will change to **Available** and the instance type will change to **Primary/Standby**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211587.png
