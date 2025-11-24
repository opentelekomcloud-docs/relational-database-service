:original_name: rds_sqlserver_05_0050.html

.. _rds_sqlserver_05_0050:

Changing a Storage Type
=======================

Scenarios
---------

If the storage type of your DB instance does not match your workloads, you can change it as needed.

Constraints
-----------

-  If the storage type of a read replica is different from that of its associated DB instance, the data synchronization may be affected. Ensure that the storage type of the read replica is the same as or faster than that of the primary DB instance.

-  During the storage type change, operations such as changing the instance class and scaling up storage space cannot be performed on the instance.
-  Changing the storage type may affect storage performance, so the storage type should be changed during off-peak hours.
-  Changing the storage type may take several minutes, hours, or even days. The time required depends on the throughput, storage space, and original storage type. This operation cannot be paused.
-  In rare cases, the change may fail due to resource problems. If this happens, you are advised to perform the change again.

Supported Storage Types
-----------------------

.. table:: **Table 1** Storage types

   ===================== ========================
   Original Storage Type Target Storage Type
   ===================== ========================
   Ultra-high I/O        Cloud SSD or extreme SSD
   Cloud SSD             Extreme SSD
   Extreme SSD           Cloud SSD
   ===================== ========================

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Change Instance Class** in the **Operation** column.

   Alternatively, click the target DB instance to go to the **Overview** page. Under **Instance Class**, click **Configure**.

#. On the displayed page, select a new storage type and click **Next**.

#. Confirm the new storage type. Click **Submit**.

#. Check the results.

   Return to the **Instances** page. A few minutes later, click the instance name and check the new storage type on the displayed **Overview** page.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
