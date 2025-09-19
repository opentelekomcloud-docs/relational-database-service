:original_name: rds_sqlserver_05_0029.html

.. _rds_sqlserver_05_0029:

Configuring Autoscaling
=======================

Scenarios
---------

With storage autoscaling enabled, when RDS detects that you are running out of database space, it automatically scales up your storage.

Autoscaling up the storage space of a read replica does not affect that of the primary DB instance. Therefore, you can separately autoscale read replicas to meet service requirements. New storage space of read replicas after autoscaling up must be greater than or equal to that of the primary DB instance.

Constraints
-----------

-  The maximum allowed storage is 4,000 GB.

-  For primary/standby DB instances, autoscaling the storage for the primary DB instance will also autoscale the storage for the standby DB instance.
-  Storage autoscaling is unavailable when the DB instance is changing instance class or rebooting.
-  Storage of RDS for SQL Server instances cannot be scaled down. Exercise caution when enabling autoscaling.
-  There is an upper limit on storage autoscaling. A maximum of two scale-ups are allowed within one hour and a maximum of five scale-ups within one day. If an instance scales up multiple times within a short period of time due to a sharp increase of temporary databases or log files, to reduce the storage usage, you can shrink the databases or log files.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region.
#. Click **Service List**. Under **Database**, click **Relational Database Service**.
#. On the **Instances** page, click the target DB instance or read replica (click |image2| in front of a DB instance to locate the read replica).
#. In the **Storage Space** area, click **Configure Autoscaling**.
#. In the displayed dialog box, set the following parameters.

   .. table:: **Table 1** Parameter description

      +---------------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | Parameter                             | Description                                                                                                       |
      +=======================================+===================================================================================================================+
      | Enable autoscaling                    | If you turn the toggle switch on, autoscaling is enabled.                                                         |
      +---------------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | Trigger If Available Storage Drops To | If the available storage drops to a specified threshold (10%, 15%, or 20%) or 10 GB, autoscaling is triggered.    |
      +---------------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | Autoscaling Limit                     | The default value range is from 40 GB to 4,000 GB. The limit must be no less than the storage of the DB instance. |
      +---------------------------------------+-------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001633304538.png
.. |image2| image:: /_static/images/en-us_image_0000001954623816.png
