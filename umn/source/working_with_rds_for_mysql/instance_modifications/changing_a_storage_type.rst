:original_name: rds_05_0140.html

.. _rds_05_0140:

Changing a Storage Type
=======================

Scenarios
---------

If the storage type of your RDS DB instance does not match your workloads, you can change it as needed.

Constraints
-----------

.. table:: **Table 1** Constraints

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Phase                             | Constraints                                                                                                                                                                                                                                              |
   +===================================+==========================================================================================================================================================================================================================================================+
   | Before the change                 | -  The storage type of an instance can be changed only when the instance is in the **Available** state.                                                                                                                                                  |
   |                                   | -  Changing the storage type may affect storage performance, so the storage type should be changed during off-peak hours.                                                                                                                                |
   |                                   | -  If the storage type of a read replica is different from that of its associated DB instance, the data synchronization may be affected. Ensure that the storage type of the read replica is the same as or faster than that of the primary DB instance. |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | During the change                 | Changing a storage type takes several minutes or even hours, depending on the throughput, storage space, original storage type, and new storage type.                                                                                                    |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | After the change                  | In rare cases, a storage type may fail to be changed due to a backend issue. If this happens, try again later.                                                                                                                                           |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Storage types

   +-----------------------+-----------------------+--------------------------+
   | Instance Type         | Original Storage Type | Target Storage Type      |
   +=======================+=======================+==========================+
   | -  Primary/Standby    | Cloud SSD             | Extreme SSD              |
   | -  Read Replica       |                       |                          |
   | -  Single             |                       |                          |
   +-----------------------+-----------------------+--------------------------+
   |                       | Ultra-high I/O        | Cloud SSD or extreme SSD |
   +-----------------------+-----------------------+--------------------------+

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate a DB instance using cloud SSD and choose **More** > **Change Instance Class** in the **Operation** column.

   Alternatively, click the instance name to go to the **Overview** page. Under **Instance Class**, click **Configure**.

#. On the displayed page, select **Extreme SSD** for **Storage Type** and click **Next**.

#. Confirm the new storage type. Click **Submit**.

#. Check the results.

   Return to the **Instances** page. A few minutes later, click the instance name and check the new storage type on the displayed **Overview** page.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
