:original_name: rds_faq_0065.html

.. _rds_faq_0065:

How Does a Cloud Database Perform a Primary/Standby Switchover?
===============================================================

RDS provides the high availability. Select the primary/standby mode.

Failover
--------

Also called an unplanned handover. If the primary DB instance fails, the system will automatically switch to the standby DB instance within 5 minutes. No human intervention is required. The connection IP address remains unchanged. DB instances cannot be accessed during the failover. You need to configure automatic reconnections between applications and RDS DB instances to ensure near-continuous availability.

Switchover (Manual)
-------------------

Also called a planned handover. When a DB instance is running properly, you can manually perform a primary/standby switchover if it is needed.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the **DB Information** area on the displayed **Basic Information** page, click **Switch** in the **DB Instance Type** field.

   Alternatively, click |image2| in the DB instance topology on the **Basic Information** page to manually trigger a primary/standby switchover.

   .. important::

      A primary/standby switchover may cause service interruption for some seconds or minutes (depending on the replication delay). If the replication delay is too long, a small amount of data may be lost. To prevent traffic congestion, perform a switchover during off-peak hours.

#. In the **Switch Primary/Standby Instances** dialog box, click **Yes** to switch between the primary and standby DB instances.

   If the replication status is **Available** and the replication delay is greater than 300s, the primary/standby switchover task cannot be delivered.

#. After a switchover is successful, you can view and manage the DB instance on the **Instances** page.

   -  During the switchover process, the DB instance status is **Switchover in progress**.
   -  In the upper right corner of the DB instance list, click |image3| to refresh the list. After the switchover is complete, the DB instance status will become **Available**

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001470260209.png
.. |image3| image:: /_static/images/en-us_image_0000001470340233.png
