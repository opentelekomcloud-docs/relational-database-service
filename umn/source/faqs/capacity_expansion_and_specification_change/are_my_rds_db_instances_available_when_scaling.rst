:original_name: rds_faq_0016.html

.. _rds_faq_0016:

Are My RDS DB Instances Available When Scaling?
===============================================

Currently, you can scale up storage space and change the CPU or memory of a DB instance.

-  When storage space is being scaled up, RDS DB instances are still available and services are not affected. However, you cannot delete or reboot DB instances that are being scaled.

-  When the CPU or memory of DB instances is being changed, the network is intermittently disconnected once or twice within a few seconds. (For Microsoft SQL Server 2017 Enterprise Edition, you need to stop services first and then change the CPU or memory of DB instances.) For primary/standby DB instances, a failover may occur and services may be briefly interrupted. Changing the CPU or memory takes 5 to 15 minutes.

   After you change the CPU or memory, the DB instances will reboot and services will be interrupted. Therefore, select off-peak hours to perform this operation. Rebooting a DB instance will clear the cached memory in it. You are advised to reboot it during off-peak hours.
