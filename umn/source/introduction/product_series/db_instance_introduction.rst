:original_name: rds_01_0010.html

.. _rds_01_0010:

DB Instance Introduction
========================

Currently, RDS DB instances are classified into the following types:

-  Single
-  Primary/Standby

Different series support different DB engines and instance specifications.

.. _rds_01_0010__table15359933192816:

.. table:: **Table 1** DB instance types

   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | DB Instance Type      | Description                                                                                            | Scenarios                                                                                                                    |
   +=======================+========================================================================================================+==============================================================================================================================+
   | Single                | Uses a single-node architecture. More cost-effective than the mainstream primary/standby DB instances. | -  Personal learning                                                                                                         |
   |                       |                                                                                                        | -  Microsites                                                                                                                |
   |                       |                                                                                                        | -  Development and testing environment of small- and medium-sized enterprises                                                |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Primary/Standby       | Uses an HA architecture with one master node and one slave node.                                       | -  Production databases of large- and medium-sized enterprises                                                               |
   |                       |                                                                                                        | -  Applications for the Internet, Internet of Things (IoT), retail e-commerce sales, logistics, gaming, and other industries |
   |                       | The primary and standby DB instances share the same IP address and can be deployed in different AZs.   |                                                                                                                              |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
