:original_name: rds_11_0023.html

.. _rds_11_0023:

Restoring from Backup Files to RDS for SQL Server
=================================================

Scenarios
---------

This section describes how to use an automated or manual backup to restore a DB instance to the status when the backup was created.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Backups & Restorations** page, locate the target backup and click **Restore** in the **Operation** column.

   Alternatively, click the target DB instance on the **Instances** page. On the displayed page, choose **Backups & Restorations**. On the displayed page, select the target backup to be restored and click **Restore** in the **Operation** column.

#. In the displayed dialog box, configure required information and click **OK**.

   a. Select a restoration method and click **OK**.

      -  Create New Instance

         The **Create New Instance** page is displayed.

         -  The DB engine of the new DB instance is the same as that of the original DB instance and cannot be changed.

         -  The original DB instance can be restored to the same or a later DB engine version, as shown in :ref:`Table 1 <rds_11_0023__table1334944713437>`.

            .. _rds_11_0023__table1334944713437:

            .. table:: **Table 1** Restoring to specific DB engine versions

               +-----------------------------------+-----------------------------------+
               | Original DB Engine Version        | Restore To                        |
               +===================================+===================================+
               | 2017 Standard Edition             | 2017 Standard Edition             |
               |                                   |                                   |
               |                                   | 2017 Enterprise Edition           |
               |                                   |                                   |
               |                                   | 2019 Standard Edition             |
               |                                   |                                   |
               |                                   | 2019 Enterprise Edition           |
               +-----------------------------------+-----------------------------------+
               | 2017 Enterprise Edition           | 2017 Enterprise Edition           |
               |                                   |                                   |
               |                                   | 2019 Enterprise Edition           |
               +-----------------------------------+-----------------------------------+
               | 2019 Standard Edition             | 2019 Standard Edition             |
               |                                   |                                   |
               |                                   | 2019 Enterprise Edition           |
               |                                   |                                   |
               |                                   | 2022 Standard Edition             |
               |                                   |                                   |
               |                                   | 2022 Enterprise Edition           |
               +-----------------------------------+-----------------------------------+
               | 2019 Enterprise Edition           | 2019 Standard Edition             |
               |                                   |                                   |
               |                                   | 2019 Enterprise Edition           |
               |                                   |                                   |
               |                                   | 2022 Enterprise Edition           |
               +-----------------------------------+-----------------------------------+
               | 2022 Standard Edition             | 2022 Standard Edition             |
               |                                   |                                   |
               |                                   | 2022 Enterprise Edition           |
               +-----------------------------------+-----------------------------------+
               | 2022 Enterprise Edition           | 2022 Standard Edition             |
               |                                   |                                   |
               |                                   | 2022 Enterprise Edition           |
               +-----------------------------------+-----------------------------------+

         -  Storage space of the new DB instance is the same as that of the original DB instance by default and the new instance must be at least as large as the original DB instance.

         -  Other settings are the same as those of the original DB instance by default and can be modified. For details, see :ref:`Step 1: Create a DB Instance <rds_04_0061>`.

      -  Restore to Original

         .. important::

            -  If the DB instance for which the backup is created has been deleted, data cannot be restored to the original DB instance.
            -  Restoring to the original DB instance will overwrite data on it and cause the original DB instance to be unavailable during the restoration.

      -  Restore to Existing

         .. important::

            -  Restoring to an existing DB instance will overwrite data on it and cause the existing DB instance to be unavailable.
            -  To restore backup data to an existing DB instance, the selected DB instance must be in the same VPC as the original DB instance and must have the same DB engine and the same or later version than the original DB instance.
            -  Ensure that the storage space of the selected DB instance is greater than or equal to the storage space of the original DB instance. Otherwise, data will not be restored.
            -  DB instances with the TDE function enabled cannot be restored from backups to existing DB instances.

         Select an existing DB instance and click **Next**.

   b. Select the databases to be restored. You can rename these databases as required. If you do not enter a new name, the original database name will be used.

      .. note::

         -  The new database names must be different from each other and must be different from the original database names.
         -  The new database names cannot contain the following fields (case-insensitive): rdsadmin, master, msdb, tempdb, model, and resource.
         -  Each database name consists of 1 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.

#. View the restoration result. The result depends on which restoration method was selected:

   -  Create New Instance

      A new DB instance is created using the backup data. The status of the DB instance changes from **Creating** to **Available**.

      The new DB instance is independent from the original one. If you need read replicas to offload read pressure, create one or more for the new DB instance.

   -  Restore to Original

      On the **Instances** page, the status of the target existing DB instance changes from **Restoring** to **Available**. If the target existing DB instance contains read replicas, the read replica status is the same as the target existing DB instance status.

      After the restoration is complete, a full backup will be automatically triggered.

   -  Restore to Existing

      On the **Instances** page, the status of the DB instance changes from **Restoring** to **Available**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
