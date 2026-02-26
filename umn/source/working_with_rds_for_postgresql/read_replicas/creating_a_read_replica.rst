:original_name: rds_add_read_replica_pg.html

.. _rds_add_read_replica_pg:

Creating a Read Replica
=======================

**Scenarios**
-------------

Read replicas are used to enhance the read capabilities and reduce the load on primary DB instances.

You can create read replicas as needed.

.. note::

   A maximum of five read replicas can be created for a primary DB instance.

   The specifications of read replicas must be greater than or equal to the specifications of the current primary DB instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the target DB instance and choose **More** > **Create Read Replica** in the **Operation** column.
#. On the displayed page, configure information about the DB instance and click **Create Now**.

   .. table:: **Table 1** Basic Settings

      +-----------+------------------------------------------------------------------------------+
      | Parameter | Description                                                                  |
      +===========+==============================================================================+
      | Region    | By default, read replicas are in the same region as the primary DB instance. |
      +-----------+------------------------------------------------------------------------------+

   .. table:: **Table 2** Engine Options

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                       |
      +===================================+===================================================================================================================================================+
      | DB Engine                         | Same as the DB engine of the primary DB instance by default and cannot be changed.                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Engine Version                 | Same as the DB engine version of the primary DB instance by default and cannot be changed.                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Type                      | Determines the DB instance read/write speed. The higher the maximum throughput is, the higher the DB instance read/write speed can be.            |
      |                                   |                                                                                                                                                   |
      |                                   | -  **Cloud SSD**: cloud drives used to decouple storage from compute. The maximum throughput is 350 MB/s.                                         |
      |                                   | -  **Extreme SSD**: uses 25GE network and RDMA technologies to provide you with up to 1,000 MB/s throughput per disk and sub-millisecond latency. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | RDS allows you to deploy primary DB instances and read replicas in a single AZ or across AZs to improve reliability.                              |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Instance Configuration

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                         |
      +===================================+=====================================================================================================================================================+
      | Instance Class                    | Refers to the CPU and memory of a DB instance. Different instance classes have different numbers of database connections and maximum IOPS.          |
      |                                   |                                                                                                                                                     |
      |                                   | For details about instance classes, see section :ref:`DB Instance Classes <rds_01_0029>`.                                                           |
      |                                   |                                                                                                                                                     |
      |                                   | After a DB instance is created, you can change its CPU and memory. For details, see section :ref:`Changing a DB Instance Class <rds_pg_scale_rds>`. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Space                     | Contains the file system overhead required for inode, reserved block, and database operation.                                                       |
      |                                   |                                                                                                                                                     |
      |                                   | By default, storage space of a read replica is the same as that of the primary DB instance.                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Disk Encryption                   | Enabling disk encryption enhances data security but reduces the database's read and write performance by 5%.                                        |
      |                                   |                                                                                                                                                     |
      |                                   | **Key Name**: indicates the tenant key. Select one from the drop-down list.                                                                         |
      |                                   |                                                                                                                                                     |
      |                                   | After disk encryption is enabled, the following restrictions apply:                                                                                 |
      |                                   |                                                                                                                                                     |
      |                                   | -  If you enable disk encryption during instance creation, the disk encryption status and the key cannot be changed later.                          |
      |                                   | -  Enabling disk encryption will not encrypt backup data stored in Object Storage Service (OBS).                                                    |
      |                                   | -  Keep the key secure. Once the key is disabled, deleted, or frozen, your instance will be inaccessible and its data may not be restored.          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 4** Basic Settings

      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Description                                                                                                                                                     |
      +==================+=================================================================================================================================================================+
      | DB Instance Name | Must start with a letter and consist of 4 to 64 characters. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_). |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 5** Connectivity

      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter      | Description                                                                                                                                                                                                                                                                     |
      +================+=================================================================================================================================================================================================================================================================================+
      | VPC            | Same as the primary DB instance's VPC.                                                                                                                                                                                                                                          |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet         | Same as the primary DB instance's subnet. A floating IP address is automatically assigned when you create a read replica. You can also enter an unused floating IP address in the subnet CIDR block. After the read replica is created, you can change the floating IP address. |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group | Same as the primary DB instance's VPC.                                                                                                                                                                                                                                          |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 6** Additional Options

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================+
      | Tag                               | Tags an RDS DB instance. This configuration is optional. Adding tags to RDS DB instances helps you better identify and manage the DB instances. A maximum of 20 tags can be added for each DB instance. |
      |                                   |                                                                                                                                                                                                         |
      |                                   | After a DB instance is created, you can view its tag details on the **Tags** page. For details, see section :ref:`Managing Tags <rds_pg_tag>`.                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm specifications.

   -  If you need to modify your settings, click **Previous**.
   -  If you do not need to modify your settings, click **Submit**.

#. After a read replica has been created, you can view and manage it on the **Instances** page by clicking |image2| on the left of the DB instance to which it belongs.

Follow-up Operations
--------------------

:ref:`Managing a Read Replica <rds_pg_11_0004>`

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000002509454071.png
