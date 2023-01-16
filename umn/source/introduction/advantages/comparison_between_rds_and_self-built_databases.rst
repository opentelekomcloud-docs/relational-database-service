:original_name: rds_01_0006.html

.. _rds_01_0006:

Comparison Between RDS and Self-Built Databases
===============================================

Performance
-----------

+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Item                             | Cloud Database RDS                                                                         | Self-Built Database Service                                                                                                 |
+==================================+============================================================================================+=============================================================================================================================+
| Service availability             | For details, see the *Elastic Cloud Service User Guide*.                                   | Requires device procurement, primary/standby relationship setup, and RAID setup.                                            |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Data reliability                 | For more information, see the *Elastic Volume Service User Guide*.                         | Requires device procurement, primary/standby relationship setup, and RAID setup.                                            |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| System security                  | Defends against Anti-DDoS attacks and promptly repairs database security vulnerabilities.  | Requires procurement of expensive devices and software, as well as manual detection and repair of security vulnerabilities. |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Database backup                  | Supports automated backups, manual backups, and custom backup retention periods.           | Requires device procurement, setup, and maintenance.                                                                        |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Hardware and software investment | Supports on-demand pricing and scaling without requiring hardware and software investment. | Requires large investment in database servers. The Microsoft SQL Server license must be paid for separately.                |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| System hosting                   | Not required.                                                                              | Requires two servers for primary/standby DB instances.                                                                      |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Maintenance cost                 | Not required.                                                                              | Requires large manpower investment and professional database administrator (DBA) for maintenance.                           |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Deployment and scaling           | Supports elastic scaling, fast upgrade, and on-demand enabling.                            | Requires procurement, deployment, and coordination of hardware that matches original devices.                               |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Resource utilization             | Bills users based on the resources actually used, resulting in 100% resource utilization.  | Considers peak traffic, resulting in low resource utilization.                                                              |
+----------------------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
