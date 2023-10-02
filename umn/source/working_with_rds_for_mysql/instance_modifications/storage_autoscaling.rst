:original_name: rds_05_0039.html

.. _rds_05_0039:

Storage Autoscaling
===================

Scenarios
---------

With storage autoscaling enabled, when RDS detects that you are running out of database space, it automatically scales up your storage.

Autoscaling up the storage of a read replica does not affect that of the primary DB instance. Therefore, you can separately autoscale read replicas to meet service requirements. New storage space of read replicas after autoscaling up must be greater than or equal to that of the primary DB instance.

You can enable storage autoscaling in either of the following ways:

-  Enable this function when you create a DB instance. For details, see :ref:`Step 1: Create a DB Instance <rds_02_0008>`.
-  Enable this function after you create a DB instance. See the operations provided in this section.

Constraints
-----------

-  The storage space can be scaled up automatically only when your instance status is **Available** or **Storage full**.
-  Storage autoscaling for RDS for MySQL DB instances is supported only for common I/O and ultra-high I/O storage types.
-  The maximum allowed storage is 4,000 GB.
-  For primary/standby DB instances, autoscaling the storage for the primary DB instance will also autoscale the storage for the standby DB instance.
-  Storage autoscaling is unavailable when the DB instance is in any of the following statuses: changing instance class, upgrading a minor version, migrating the standby DB instance, and rebooting.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance or read replica (click |image2| in front of a DB instance to locate the read replica).
#. In the **Storage Space** area, click **Configure Autoscaling**.
#. In the displayed dialog box, set the following parameters:

   .. table:: **Table 1** Parameter description

      +---------------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | Parameter                             | Description                                                                                                       |
      +=======================================+===================================================================================================================+
      | Enable autoscaling                    | If you select this option, autoscaling is enabled.                                                                |
      +---------------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | Trigger If Available Storage Drops To | If the available storage drops to a specified threshold or 10 GB, autoscaling is triggered.                       |
      +---------------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | Autoscaling Limit                     | The default value range is from 40 GB to 4,000 GB. The limit must be no less than the storage of the DB instance. |
      +---------------------------------------+-------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001520982189.png
