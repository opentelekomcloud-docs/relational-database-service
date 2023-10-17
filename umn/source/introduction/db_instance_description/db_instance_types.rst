:original_name: rds_01_0016.html

.. _rds_01_0016:

DB Instance Types
=================

The smallest management unit of RDS is the DB instance. A DB instance is an isolated database environment on the cloud. Each DB instance can contain multiple user-created databases, and you can access a DB instance using the same tools and applications that you use with a stand-alone DB instance. You can create and modify DB instances using the management console or APIs. RDS does not have limits on the number of running DB instances. Each DB instance has a DB instance identifier.

DB instances are classified into the following types.

.. table:: **Table 1** DB instance types

   +------------------+------------------------------------------------------------------------------------------------------------------+
   | DB Instance Type | Description                                                                                                      |
   +==================+==================================================================================================================+
   | Single           | Uses a single-node architecture. More cost-effective than primary/standby DB instances.                          |
   +------------------+------------------------------------------------------------------------------------------------------------------+
   | Primary/Standby  | Uses an HA architecture with one master node and one slave node. The instance classes of the nodes are the same. |
   +------------------+------------------------------------------------------------------------------------------------------------------+
   | Read replica     | Uses a single-node architecture (without a standby node).                                                        |
   +------------------+------------------------------------------------------------------------------------------------------------------+

RDS for SQL Server 2019 Enterprise Edition and 2017 Enterprise Edition support read replicas.

You can use RDS to create and manage DB instances running various DB engines.

For details about differences and function comparison between different instance types, see :ref:`DB Instance Introduction <rds_01_0010>` and :ref:`Function Comparison <rds_00_0011>`.
