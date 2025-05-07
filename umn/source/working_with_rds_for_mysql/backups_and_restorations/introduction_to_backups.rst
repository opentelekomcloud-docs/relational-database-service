:original_name: rds_08_0024.html

.. _rds_08_0024:

Introduction to Backups
=======================

What Are Database Backups?
--------------------------

RDS for MySQL automatically creates backups for DB instances during the backup time window. The backups are stored based on a preset retention period (1 to 732 days).

A backup file is generated each time a backup is complete. If the instance fails or data is damaged, you can use the backup file to restore the instance, ensuring data reliability.

Backup Types
------------

RDS for MySQL supports multiple backup types. For details, see :ref:`Backup Types <en-us_topic_backup_restore>`.

Where Data Is Backed Up
-----------------------

-  Single-node instance

   A single-node architecture, which is more cost-effective than mainstream primary/standby DB instances. After a backup is triggered, data is backed up from the primary instance and stored as a package on OBS. The backup does not take up storage space of the instance.

-  Primary/standby instance

   An HA architecture. In a primary/standby pair, each instance has the same instance class. After a backup task is triggered, data is backed up from the standby instance (or from the primary instance only when there is a long primary/standby replication delay) and stored as a package on OBS. The backup does not take up storage space of the instance.

   If a database or table in the primary instance is maliciously or mistakenly deleted, the database or table in the standby instance will also be deleted. In this case, you can only use backups to restore the deleted data.

How Data Is Backed Up
---------------------

RDS for MySQL automated backup is enabled by default and cannot be disabled. RDS for MySQL performs automated full backups based on the time window and interval specified in the backup policy. It also backs up data modifications made after the most recent automated full or binlog backup every 5 minutes or when a certain amount of incremental data is generated. When you restore an instance to a point in time, the most recent full backup will be downloaded from OBS for restoration. After the restoration is complete, binlog backups will be replayed to the specified point in time.


.. figure:: /_static/images/en-us_image_0000002289561469.png
   :alt: **Figure 1** How data is backed up

   **Figure 1** How data is backed up

Backup Compression Ratio
------------------------

RDS uses `sysbench <https://github.com/akopytov/sysbench>`__ to import data models and a certain amount of data. After data is backed up, the compression ratio is about 80%. The more duplicate data there is, the higher the compression ratio is.

Compression ratio = Space occupied by backup files/Space occupied by data files x 100%

Deleting Backups
----------------

-  Manual backups and automated backups can be deleted in different ways:

   -  Manual backups can only be manually deleted.
   -  Automated backups cannot be manually deleted. To delete them, you can adjust the retention period specified in your :ref:`automated backup policy <rds_08_0004>`. When the retention period expires, automated backups will be deleted.

-  Local binlogs

   If the retention period is set to **0**, the binlogs of your DB instance will be deleted once they are synchronized to the standby instance and read replicas and successfully backed up to OBS.

   If the retention period is set to a value greater than 0, for example, 1 day, the binlogs will be retained for one day after they are synchronized to the standby instance and read replicas from the primary instance and successfully backed up to OBS. After the retention period expires, the binlogs will be automatically deleted.
