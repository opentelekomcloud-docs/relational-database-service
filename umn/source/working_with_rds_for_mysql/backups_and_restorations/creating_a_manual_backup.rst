:original_name: rds_08_0005.html

.. _rds_08_0005:

Creating a Manual Backup
========================

Scenarios
---------

RDS allows you to create manual backups of a running primary DB instance. You can use these backups to restore data.

.. note::

   When you delete a DB instance, its automated backups are also deleted but its manual backups are retained.

Constraints
-----------

-  The number of tables in a DB instance affects the backup speed. The maximum number of tables is 500,000.
-  The system verifies the connection to the DB instance when starting a full backup task. If either of the following conditions is met, the verification fails and a retry is automatically performed. If the retry fails, the backup will fail.

   -  DDL operations are being performed on the DB instance.
   -  The backup lock failed to be obtained from the DB instance.

Method 1
--------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Create Backup** in the **Operation** column.

#. In the displayed dialog box, enter a backup name and description. Then, click **OK**. If you want to cancel the backup creation task, click **Cancel**.

   -  The backup name must consist of 4 to 64 characters and start with a letter. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).
   -  The description consists of a maximum of 256 characters and cannot contain carriage return characters or the following special characters: >!<"&'=
   -  The time required for creating a manual backup depends on the amount of data.

#. After a manual backup has been created, you can view and manage it on the **Backups** page.

   Alternatively, click the target DB instance. On the **Backups & Restorations** page, you can view and manage the manual backups.

Method 2
--------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. On the **Backups & Restorations** page, click **Create Backup**. In the displayed dialog box, enter a backup name and description and click **OK**. If you want to cancel the backup creation task, click **Cancel**.

   -  The backup name must consist of 4 to 64 characters and start with a letter. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).
   -  The description consists of a maximum of 256 characters and cannot contain carriage return characters or the following special characters: >!<"&'=
   -  The time required for creating a manual backup depends on the amount of data.

#. After a manual backup has been created, you can view and manage it on the **Backups** page.

   Alternatively, click the target DB instance. On the **Backups & Restorations** page, you can view and manage the manual backups.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211679.png
