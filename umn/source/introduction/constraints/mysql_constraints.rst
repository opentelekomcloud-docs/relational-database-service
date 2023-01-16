:original_name: rds_02_0002.html

.. _rds_02_0002:

MySQL Constraints
=================

:ref:`Table 1 <rds_02_0002__table60364850123535>` shows the constraints designed to ensure the stability and security of RDS for MySQL.

.. _rds_02_0002__table60364850123535:

.. table:: **Table 1** Function constraints

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function Item                     | Constraints                                                                                                                                                                                                          |
   +===================================+======================================================================================================================================================================================================================+
   | Database access                   | -  If public accessibility is not enabled, the RDS DB instance must be in the same VPC as the ECS.                                                                                                                   |
   |                                   |                                                                                                                                                                                                                      |
   |                                   | -  RDS read replicas must be created in the same subnet as the primary DB instance.                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                      |
   |                                   | -  The security group must allow access from the ECS.                                                                                                                                                                |
   |                                   |                                                                                                                                                                                                                      |
   |                                   |    By default, RDS cannot be accessed through an ECS in a different security group. You need to add an inbound rule to the RDS security group.                                                                       |
   |                                   |                                                                                                                                                                                                                      |
   |                                   | -  The default MySQL port is **3306**. You can change it if you want to access MySQL through another port.                                                                                                           |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deployment                        | ECSs in which DB instances are deployed are not visible to users. You can access the DB instances only through an IP address and a port number.                                                                      |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database root permissions         | Only the **root** user permissions are provided on the instance creation page.                                                                                                                                       |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database parameter modification   | Most parameters can be modified on the RDS console.                                                                                                                                                                  |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data migration                    | Use MySQL CLI tools to migrate data by referring to :ref:`Migrating Data to RDS for MySQL Using mysqldump <rds_migration_mysql>`.                                                                                    |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | MySQL storage engine              | For details, see :ref:`What Storage Engines Does the RDS for MySQL Support? <rds_faq_0041>`                                                                                                                          |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database replication setup        | RDS for MySQL uses a primary/standby dual-node replication cluster. You do not need to set up replication additionally. The standby DB instance is not visible to users and therefore you cannot access it directly. |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Minor version upgrade             | Currently, RDS for MySQL supports a maximum of 100,000 tables. If the number of tables is greater than 100,000, the minor version upgrade may fail.                                                                  |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DB instance reboot                | RDS DB instances cannot be rebooted through commands. They must be rebooted through the RDS console.                                                                                                                 |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | RDS backup files                  | For details, see :ref:`Downloading a Backup File <rds_08_0006>`.                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                      |
   |                                   | You can rebuild a DB instance from the recycle bin to restore data.                                                                                                                                                  |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
