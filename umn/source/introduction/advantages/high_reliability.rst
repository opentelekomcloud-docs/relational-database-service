:original_name: rds_01_0005.html

.. _rds_01_0005:

High Reliability
================

Dual-Host Hot Standby
---------------------

RDS uses the hot standby architecture, in which failover upon fault occurrence takes only some seconds.

Data Backup
-----------

RDS automatically backs up data every day and transfers backup files to Object Storage Service (OBS). The backup files can be stored for 732 days and can be restored with just a few clicks. You can set a custom backup policy and create manual backups at any time.

Data Restoration
----------------

You can restore data from backups to any point in time during the backup retention period. In most scenarios, you can use backup files to restore data to a new DB instance at any time point within 732 days. After the data is verified, data can be migrated back to the primary DB instance.

Deleted DB instances can be moved to the recycle bin. You can rebuild the DB instance that was deleted up to 7 days ago from the recycle bin.
