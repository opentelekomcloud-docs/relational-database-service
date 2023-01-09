:original_name: rds_09_0032.html

.. _rds_09_0032:

Replicating a Backup
====================

**Scenarios**
-------------

This section describes how to replicate a manual or an automated backup. The new backup name must be different from the original backup name.

Constraints
-----------

You can replicate backups and use them only within the same region.

Backup Retention Policy
-----------------------

-  RDS will delete automated backups when they expire or the DB instance for which the backups are created is deleted.
-  If you want to retain the automated backups for a long time, you can replicate them to generate manual backups, which will be always retained until you delete them.
-  If the storage occupied by manual backups exceeds the provisioned free backup storage, additional storage costs may incur.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance. On the **Backups & Restorations** page, locate the target backup to be replicated and click **Replicate** in the **Operation** column.

   Alternatively, choose **Backup Management**. On the displayed page, locate the manual backup to be replicated and choose **More** > **Replicate** or locate an automated backup and click **Replicate** in the **Operation** column.

#. In the displayed dialog box, enter a new backup name and description and click **OK**.

   -  The backup name must consist of 4 to 64 characters and start with a letter. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).
   -  The description consists of a maximum of 256 characters and cannot contain the following special characters: >!<"&'=

#. After the new backup has been created, you can view and manage it on the **Backup Management** page.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
