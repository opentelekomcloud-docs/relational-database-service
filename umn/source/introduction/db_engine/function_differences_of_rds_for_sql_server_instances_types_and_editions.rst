:original_name: rds_01_0018.html

.. _rds_01_0018:

Function Differences of RDS for SQL Server Instances Types and Editions
=======================================================================

This section describes function differences between single and primary/standby DB instances as well as function differences among Microsoft SQL Server editions.

-  For details about differences of basic functions, see :ref:`Table 1 <rds_01_0018__table45712140181049>`.
-  For details about differences of DB instance types, see :ref:`Table 1 <rds_01_0010__table15359933192816>`.
-  For details about differences of database migration functions, see :ref:`Table 2 <rds_01_0018__table51069553181111>`.
-  For details about differences of database security functions, see :ref:`Table 3 <rds_01_0018__table12903168181132>`.

.. _rds_01_0018__table45712140181049:

.. table:: **Table 1** Differences of basic functions

   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   | Module                   | Function Item                      | Primary/Standby | Single        | Cluster       |
   +==========================+====================================+=================+===============+===============+
   | Life cycle               | Create a DB instance               | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Reboot a DB instance               | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Auto-renewal                       | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Change the instance class          | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Delete a DB instance               | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Upgrade the DB engine version      | Not supported   | Not supported | Not supported |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Restore to a new DB instance       | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Create a read replica              | Not supported   | Not supported | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Recycle bin                        | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   | DB instance properties   | View the DB instance list          | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | View DB instance details           | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Modify the DB instance description | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Change the maintenance window      | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Manage tags                        | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   | Database connection      | Internal access through a VPC      | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Public accessibility               | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Read/write splitting               | Not supported   | Not supported | Not supported |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   | Backups and restorations | Full backup                        | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Log backup                         | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Customize a backup policy          | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Restore from automated backups     | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Point-in-time restore              | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Partial backup                     | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Partial restore                    | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   | Monitoring and alarms    | Resource monitoring                | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | DB engine monitoring               | Not supported   | Not supported | Not supported |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Customize monitoring policies      | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Aggregate monitoring items         | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   | Parameter management     | Parameter update                   | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | Parameter template                 | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   | Log management           | Error logs                         | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+
   |                          | System running logs                | Supported       | Supported     | Supported     |
   +--------------------------+------------------------------------+-----------------+---------------+---------------+

.. _rds_01_0018__table51069553181111:

.. table:: **Table 2** Differences of database migration

   ============================ =============== =============
   Function Item                Primary/Standby Single
   ============================ =============== =============
   Homogeneous data migration   Supported       Supported
   Heterogeneous data migration Not supported   Not supported
   Data synchronization         Supported       Supported
   ============================ =============== =============

.. _rds_01_0018__table12903168181132:

.. table:: **Table 3** Differences of database security

   +----------------------------------------------+--------------------------------+--------------------------------+
   | Function Item                                | Primary/Standby                | Single                         |
   +==============================================+================================+================================+
   | IP address whitelist                         | Not supported                  | Not supported                  |
   +----------------------------------------------+--------------------------------+--------------------------------+
   | Management audit                             | Supported                      | Supported                      |
   +----------------------------------------------+--------------------------------+--------------------------------+
   | Storage encryption                           | Supported                      | Supported                      |
   +----------------------------------------------+--------------------------------+--------------------------------+
   | Network encryption                           | Supported                      | Supported                      |
   +----------------------------------------------+--------------------------------+--------------------------------+
   | Security group management                    | Supported                      | Supported                      |
   +----------------------------------------------+--------------------------------+--------------------------------+
   | Transparent Data Encryption (TDE) encryption | Supported (Enterprise Edition) | Supported (Enterprise Edition) |
   +----------------------------------------------+--------------------------------+--------------------------------+

:ref:`Table 4 <rds_01_0018__table38343542181154>` lists the major differences of the official Microsoft SQL Server editions.

For more information about function differences among Microsoft SQL Server 2017 official editions, see `official documents <https://learn.microsoft.com/en-us/sql/sql-server/editions-and-components-of-sql-server-2017?view=sql-server-2017>`__.

For more information about function differences among Microsoft SQL Server 2019 official editions, see `official documents <https://learn.microsoft.com/en-us/sql/sql-server/editions-and-components-of-sql-server-2019?view=sql-server-2017>`__.

.. _rds_01_0018__table38343542181154:

.. table:: **Table 4** Differences of Microsoft SQL Server editions

   +---------------------------------------------+------------------+--------------------+
   | Function Item                               | Standard Edition | Enterprise Edition |
   +=============================================+==================+====================+
   | High availability                           | Mirror HA        | Mirror HA          |
   +---------------------------------------------+------------------+--------------------+
   | Data compression                            | Supported        | Supported          |
   +---------------------------------------------+------------------+--------------------+
   | SQL Profiler                                | Supported        | Supported          |
   +---------------------------------------------+------------------+--------------------+
   | Column index                                | Supported        | Supported          |
   +---------------------------------------------+------------------+--------------------+
   | Change Data Capture (CDC)                   | Not supported    | Supported          |
   +---------------------------------------------+------------------+--------------------+
   | Online DDL                                  | Not supported    | Supported          |
   +---------------------------------------------+------------------+--------------------+
   | Parallel searches                           | Not supported    | Supported          |
   +---------------------------------------------+------------------+--------------------+
   | Adjustment of partitioned table parallelism | Not supported    | Supported          |
   +---------------------------------------------+------------------+--------------------+
   | TDE                                         | Not supported    | Supported          |
   +---------------------------------------------+------------------+--------------------+
   | Advanced R integration                      | Not supported    | Supported          |
   +---------------------------------------------+------------------+--------------------+
