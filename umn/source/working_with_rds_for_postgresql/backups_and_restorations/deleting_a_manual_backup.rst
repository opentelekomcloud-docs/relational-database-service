:original_name: rds_09_0033.html

.. _rds_09_0033:

Deleting a Manual Backup
========================

**Scenarios**
-------------

You can delete manual backups to free up backup storage.

.. important::

   Deleted manual backups cannot be recovered. Exercise caution when performing this operation.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. In the navigation pane on the left, choose **Backup Management**. On the displayed page, locate the target manual backup to be deleted and choose **More** > **Delete** in the **Operation** column.

   The following backups cannot be deleted:

   -  Automated backups
   -  Backups that are being restored
   -  Backups that are being replicated

#. In the displayed dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
