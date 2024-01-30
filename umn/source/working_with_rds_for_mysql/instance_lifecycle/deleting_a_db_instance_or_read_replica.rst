:original_name: rds_08_0002.html

.. _rds_08_0002:

Deleting a DB Instance or Read Replica
======================================

Scenarios
---------

To release resources, you can delete DB instances or read replicas as required on the **Instances** page.

Constraints
-----------

-  DB instances cannot be deleted when operations are being performed on them. They can be deleted only after the operations are complete.
-  If you delete a DB instance, its automated backups are also deleted and you are no longer billed for them. Manual backups, however, are still retained and will generate additional costs.

.. important::

   -  If you delete a primary DB instance, its standby DB instance and read replicas (if any) are also deleted automatically. Exercise caution when performing this operation.
   -  Deleted DB instances cannot be recovered and resources are released. Exercise caution when performing this operation. If you want to retain data, :ref:`create a manual backup <rds_08_0005>` first before deleting the DB instance.
   -  You can restore a DB instance that was deleted up to 7 days ago from the recycle bin. For details, see :ref:`Recycling a DB Instance <rds_mysql_recycle>`.
   -  You can use a manual backup to restore a DB instance. For details, see :ref:`Restoring from Backup Files to DB Instances <rds_08_0007>`.

Deleting a DB Instance
----------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the primary DB instance to be deleted and click **More** > **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the DB instance list later to confirm that the deletion was successful.

Deleting a Read Replica
-----------------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the target DB instance and click |image3|. All the read replicas created for the DB instance are displayed.
#. Locate the read replica to be deleted and click **More** > **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
#. Refresh the DB instance list later to check that the deletion is successful.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
.. |image2| image:: /_static/images/en-us_image_0000001786854381.png
.. |image3| image:: /_static/images/en-us_image_0000001786934157.png
