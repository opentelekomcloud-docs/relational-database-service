:original_name: rds_sqlserver_backup_restore.html

.. _rds_sqlserver_backup_restore:

Working with Backups
====================

RDS supports DB instance backups and restorations to ensure data reliability.

Automated Backups
-----------------

Automated backups are created during the backup period of your DB instances. RDS saves automated backups based on the retention period you specified. If necessary, you can restore to any point in time during your backup retention period. For details, see :ref:`Configuring an Automated Backup Policy <rds_11_0031>`.

Manual Backups
--------------

Manual backups are user-initiated full backups of DB instances. They are retained until you delete them manually. For details, see :ref:`Creating a Manual Backup <rds_11_0010>`.

Downloading a Backup File
-------------------------

You can download a full backup file for local data backup or restoration. For details, see :ref:`Downloading a Backup File <rds_11_0013>`.
