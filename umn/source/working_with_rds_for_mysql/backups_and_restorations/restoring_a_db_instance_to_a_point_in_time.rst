:original_name: rds_08_0008.html

.. _rds_08_0008:

Restoring a DB Instance to a Point in Time
==========================================

Scenarios
---------

You can restore from automated backups to a specified point in time.

RDS for MySQL supports restoration to a new, the original, or an existing DB instance.

When you enter the time point that you want to restore the DB instance to, RDS downloads the most recent full backup file from OBS to the DB instance. Then, incremental backups are also restored to the specified point in time on the DB instance. Data is restored at an average speed of 30 MB/s.

Restoring a DB Instance
-----------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Backups & Restorations**. On the displayed page, click **Restore to Point in Time**.
#. Select the restoration date and time range, enter a time point within the selected time range, and select a restoration method. Then, click **OK**.

   -  Create New Instance

      The **Create New Instance** page is displayed.

      -  The DB engine and version of the new DB instance are the same as those of the original DB instance and cannot be changed.
      -  Other settings are the same as those of the original DB instance by default and can be modified. For details, see :ref:`Step 1: Create a DB Instance <rds_02_0008>`.

   -  Restore to Original

      a. Select "I acknowledge that after I select Restore to Original, data on the original databases will be overwritten and the original DB instance will be unavailable during the restoration." and click **Next**.
      b. Confirm the information and click **OK**.

      .. important::

         Restoring to the original DB instance will overwrite all existing data and the DB instance will be unavailable during the restoration process.

   -  Restore to Existing

      a. Select "I acknowledge that restoring to an existing DB instance will overwrite data on it and cause the existing DB instance to be unavailable during the restoration." and click **Next**.
      b. Confirm the information and click **OK**.

      .. important::

         -  Restoring to an existing DB instance will overwrite data on it and cause the existing DB instance to be unavailable.
         -  To restore backup data to an existing DB instance, the selected DB instance must use the same DB engine and the same or a later version than the original DB instance.
         -  Ensure that the storage space of the selected DB instance is greater than or equal to the storage space of the original DB instance. Otherwise, data will not be restored.

#. View the restoration result. The result depends on which restoration method was selected:

   -  Create New Instance

      A new DB instance is created using the backup data. The status of the DB instance changes from **Creating** to **Available**.

      The new DB instance is independent from the original one. If you need read replicas to offload read pressure, create one or more for the new DB instance.

      After the new DB instance is created, a full backup will be automatically triggered.

   -  Restore to Original

      On the **Instances** page, the status of the DB instance changes from **Restoring** to **Available**.

      A new restoration time range is available. There will be a difference between the new and original time ranges. This difference reflects the duration of the restoration.

      After the restoration is complete, a full backup will be automatically triggered.

   -  Restore to Existing

      On the **Instances** page, the status of the DB instance changes from **Restoring** to **Available**.

      After the restoration is complete, a full backup will be automatically triggered.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
