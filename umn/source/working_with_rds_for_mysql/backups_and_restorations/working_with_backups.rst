:original_name: en-us_topic_backup_restore.html

.. _en-us_topic_backup_restore:

Working with Backups
====================

RDS supports backups and restorations to ensure data reliability.

Automated Backups
-----------------

Automated backups are created during the backup time window for your DB instances. RDS saves automated backups based on a retention period you specify. If necessary, you can restore a DB instance to any point in time during your backup retention period. For details, see :ref:`Configuring an Automated Backup Policy <rds_08_0004>`.

Manual Backups
--------------

Manual backups are user-initiated full backups of DB instances. They are retained until you delete them manually. For details, see :ref:`Creating a Manual Backup <rds_08_0005>`.

Downloading a Backup File
-------------------------

You can download a full or an incremental backup file for local data backup or restoration. For details, see :ref:`Downloading a Backup File <rds_08_0006>` and :ref:`Downloading a Binlog Backup File <rds_03_0100>`.
