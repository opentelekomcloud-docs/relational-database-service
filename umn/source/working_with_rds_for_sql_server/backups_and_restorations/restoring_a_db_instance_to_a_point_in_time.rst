:original_name: rds_11_0022.html

.. _rds_11_0022:

Restoring a DB Instance to a Point in Time
==========================================

Scenarios
---------

You can restore from automated backups to a specified point in time.

RDS for Microsoft SQL Server supports restoration to a new, the original, or an existing DB instance.

If you delete a database or modify some records in a database at a specified time, you only need to restore the database instead of restoring the whole DB instance. You can also restore databases to a point in time as required.

When you enter the time point that you want to restore the DB instance to, RDS downloads the most recent full backup file from OBS to the DB instance. Then, incremental backups are also restored to the specified point in time on the DB instance. Data is restored at an average speed of 30 MB/s.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Backups & Restorations**. On the displayed page, click **Restore to Point in Time**.
#. In the displayed dialog box, configure required information and click **OK**.

   a. Select the time range, select or enter a time point within the acceptable range.
   b. Select a restoration method.

      -  Create New Instance

         The **Create New Instance** page is displayed.

         -  The DB engine of the new DB instance is the same as that of the original DB instance and cannot be changed.
         -  Storage space of the new DB instance is the same as that of the original DB instance by default and the new instance must be at least as large as the original DB instance.
         -  Other settings are the same as those of the original DB instance by default and can be modified. For details, see section :ref:`Step 1: Create a DB Instance <rds_04_0061>`.

      -  Restore to Original

         .. important::

            -  Restoring to the original DB instance will overwrite data on it and cause the original DB instance to be unavailable during the restoration.

      -  Restore to Existing

         .. important::

            -  Restoring to an existing DB instance will overwrite data on it and cause the existing DB instance to be unavailable.
            -  To restore backup data to an existing DB instance, the selected DB instance must be in the same VPC as the original DB instance and must have the same DB engine and the same or later version than the original DB instance.
            -  Ensure that the storage space of the selected DB instance is greater than or equal to the storage space of the original DB instance. Otherwise, data will not be restored.
            -  DB instances with the TDE function enabled cannot be restored from backups to existing DB instances.

         Select an existing DB instance and click **Next**.

   c. Select the databases to be restored. You can rename these databases as required. If you do not enter a new name, the original database name will be used.

      .. note::

         -  The new database names must be different from each other and must be different from the original database names.
         -  The new database names cannot contain the following fields (case-insensitive): rdsadmin, master, msdb, tempdb, model, and resource.
         -  Each database name consists of 1 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.

#. View the restoration result. The result depends on which restoration method was selected:

   -  Create New Instance

      A new DB instance is created using the backup data. The status of the DB instance changes from **Creating** to **Available**.

      The new DB instance is independent from the original one.

   -  Restore to Original

      On the **Instances** page, the status of the DB instance changes from **Restoring** to **Available**.

      A new restoration time range is available. There will be a difference between the new and original time ranges. This difference reflects the duration of the restoration.

   -  Restore to Existing

      On the **Instances** page, the status of the DB instance changes from **Restoring** to **Available**.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
