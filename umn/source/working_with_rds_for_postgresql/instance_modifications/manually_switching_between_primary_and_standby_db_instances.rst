:original_name: rds_pg_switch_ha.html

.. _rds_pg_switch_ha:

Manually Switching Between Primary and Standby DB Instances
===========================================================

Scenarios
---------

If you choose to create primary/standby DB instances, RDS will create a primary DB instance and a synchronous standby DB instance in the same region. You can access the primary DB instance only. The standby instance serves as a backup. You can manually promote the standby DB instance to the new primary instance for failover support.

Constraints
-----------

-  A DB instance is running properly.
-  The replication between the primary and standby instances is normal.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target primary/standby DB instance.

#. In the **Configurations** area on the displayed **Overview** page, under **DB Instance Type**, click **Switch**.

   .. important::

      A primary/standby switchover may cause service interruptions for some seconds or minutes (depending on the replication delay). If the replication delay is too long, a small amount of data may be lost. To prevent traffic congestion, you are advised to perform a switchover during off-peak hours.

#. In the displayed dialog box, click **Yes** to switch between the primary and standby DB instances.

   If the replication status is **Available** and the replication delay is greater than 300s, the primary/standby switchover task cannot be delivered.

#. After a switchover is successful, you can view and manage the DB instance on the **Instances** page.

   -  During the switchover process, the DB instance status is **Switchover in progress**.
   -  In the upper right corner of the DB instance list, click |image2| to refresh the list. After the switchover is successful, the DB instance status will become **Available**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191131421.png
