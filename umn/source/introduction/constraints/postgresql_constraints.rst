:original_name: rds_02_0012.html

.. _rds_02_0012:

PostgreSQL Constraints
======================

:ref:`Table 1 <rds_02_0012__table60364850123535>` shows the constraints designed to ensure the stability and security of RDS for PostgreSQL.

.. _rds_02_0012__table60364850123535:

.. table:: **Table 1** Function constraints

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function Item                     | Constraints                                                                                                                                                                                                               |
   +===================================+===========================================================================================================================================================================================================================+
   | Database access                   | -  If public accessibility is not enabled, the RDS DB instance must be in the same VPC as the ECS.                                                                                                                        |
   |                                   | -  RDS read replicas must be created in the same subnet as the primary DB instance.                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                           |
   |                                   | -  The security group must allow access from the ECS.                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                           |
   |                                   |    By default, RDS cannot be accessed through an ECS in a different security group. You need to add an inbound rule to the RDS security group.                                                                            |
   |                                   |                                                                                                                                                                                                                           |
   |                                   | -  The default RDS port is **5432**. You can change it if you want to access RDS through another port.                                                                                                                    |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deployment                        | ECSs in which DB instances are deployed are not visible to users. You can access the DB instances only through an IP address and a port number.                                                                           |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database root permissions         | Only the **root** user permissions are provided on the instance creation page.                                                                                                                                            |
   |                                   |                                                                                                                                                                                                                           |
   |                                   | .. note::                                                                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                                           |
   |                                   |    The **root** user has the following permissions: Create role, Create DB, and Replication.                                                                                                                              |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database parameter modification   | Most parameters can be modified on the RDS console.                                                                                                                                                                       |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data migration                    | Use psql to import data by referring to :ref:`Migrating Data to RDS for PostgreSQL Using psql <rds_09_0023>`.                                                                                                             |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database replication setup        | RDS for PostgreSQL uses a primary/standby dual-node replication cluster. You do not need to set up replication additionally. The standby DB instance is not visible to users and therefore you cannot access it directly. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DB instance reboot                | DB instances cannot be rebooted through commands. They must be rebooted through the RDS console.                                                                                                                          |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | RDS backup files                  | For details, see :ref:`Downloading a Full Backup File <rds_09_0031>`.                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                           |
   |                                   | You can rebuild a DB instance from the recycle bin to restore data.                                                                                                                                                       |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
