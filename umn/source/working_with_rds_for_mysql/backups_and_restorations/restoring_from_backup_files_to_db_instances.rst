:original_name: rds_08_0007.html

.. _rds_08_0007:

Restoring from Backup Files to DB Instances
===========================================

Scenarios
---------

This section describes how to use an automated or manual backup to restore a DB instance to the status when the backup was created. The restoration is at the DB instance level.

When you restore a DB instance from a backup file, a full backup file is downloaded from OBS and then restored to the DB instance at an average speed of 40 MB/s.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Backup Management** page, select the backup to be restored and click **Restore** in the **Operation** column.

   Alternatively, click the target DB instance on the **Instances** page. On the displayed page, choose **Backups & Restorations**. On the displayed page, select the target backup to be restored and click **Restore** in the **Operation** column.

#. Select a restoration method and click **OK**.

   -  Create New Instance

      The **Create New Instance** page is displayed.

      -  The DB engine and version of the new DB instance are the same as those of the original DB instance and cannot be changed.
      -  Storage space of the new DB instance is the same as that of the original DB instance by default and the new instance must be at least as large as the original DB instance.
      -  Other settings are the same as those of the original DB instance by default and can be modified. For details, see :ref:`Step 1: Create a DB Instance <rds_02_0008>`.

   -  Restore to Original

      a. Select "I acknowledge that after I select Restore to Original, data on the original databases will be overwritten and the original DB instance will be unavailable during the restoration." and click **Next**.
      b. Confirm the information and click **OK**.

      .. important::

         -  If the DB instance for which the backup is created has been deleted, data cannot be restored to the original DB instance.
         -  Restoring to the original DB instance will overwrite all existing data and the DB instance will be unavailable during the restoration process.

   -  Restore to Existing

      a. Select "I acknowledge that restoring to an existing DB instance will overwrite data on it and cause the existing DB instance to be unavailable during the restoration." and click **Next**.
      b. Confirm the information and click **OK**.

      .. important::

         -  If the target existing DB instance has been deleted, data cannot be restored to it.
         -  Restoring to an existing DB instance will overwrite data on it and cause the existing DB instance to be unavailable.
         -  To restore backup data to an existing DB instance, the selected DB instance must use the same DB engine and the same or a later version than the original DB instance.
         -  Ensure that the storage space of the selected existing DB instance is greater than or equal to the storage space of the original DB instance. Otherwise, data will not be restored.

#. View the restoration result. The result depends on which restoration method was selected:

   -  Create New Instance

      A new DB instance is created using the backup data. The status of the DB instance changes from **Creating** to **Available**.

      The new DB instance is independent from the original one. If you need read replicas to offload read pressure, create one or more for the new DB instance.

      After the new instance is created, a full backup will be automatically triggered.

   -  Restore to Original

      On the **Instances** page, the status of the original DB instance changes from **Restoring** to **Available**. If the original DB instance contains read replicas, the read replica status is the same as the original DB instance status.

      After the restoration is complete, a full backup will be automatically triggered.

   -  Restore to Existing

      On the **Instances** page, the status of the target existing DB instance changes from **Restoring** to **Available**. If the target existing DB instance contains read replicas, the read replica status is the same as the target existing DB instance status.

      After the restoration is complete, a full backup will be automatically triggered.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
