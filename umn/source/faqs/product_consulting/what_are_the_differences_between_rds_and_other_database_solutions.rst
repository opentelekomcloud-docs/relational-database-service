:original_name: rds_faq_0004.html

.. _rds_faq_0004:

What Are the Differences Between RDS and Other Database Solutions?
==================================================================

.. table:: **Table 1** Differences between RDS and other database solutions

   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Function                         | RDS                                                                                       | Self-Built Database Service                                                                                                 |
   +==================================+===========================================================================================+=============================================================================================================================+
   | Service availability             | For details, see Elastic Cloud Service User Guide.                                        | Requires self-guarantee, primary/standby relationship setup, and RAID setup.                                                |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Data reliability                 | For details, see *Elastic Volume Service User Guide*.                                     | Requires self-guarantee, primary/standby relationship setup, and RAID setup.                                                |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | System security                  | Defends against Anti-DDoS attacks and promptly repairs database security vulnerabilities. | Requires procurement of expensive devices and software, as well as manual detection and repair of security vulnerabilities. |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Database backup                  | Automated backup                                                                          | You need to find backup storage space by yourself and periodically check whether backup data can be restored.               |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Hardware and software investment | Supports on-demand pricing without hardware and software investment.                      | Requires large investment in database servers.                                                                              |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | System hosting                   | Not required.                                                                             | The hosting cost is high.                                                                                                   |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Maintenance cost                 | Not required.                                                                             | Full-time Database Administrators (DBAs) are required for maintenance, leading to high manpower costs.                      |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Deployment and scaling           | Supports elastic scaling, fast deployment, and on-demand enabling.                        | Requires procurement, deployment, and coordination of hardware.                                                             |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Resource utilization             | Bills users based on the resources actually used, resulting in high resource utilization. | Peak resource utilization is considered, leading to low resource usage.                                                     |
   +----------------------------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
