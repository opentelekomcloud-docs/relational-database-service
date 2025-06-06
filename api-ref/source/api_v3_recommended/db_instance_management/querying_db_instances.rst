:original_name: rds_01_0004.html

.. _rds_01_0004:

Querying DB Instances
=====================

Function
--------

This API is used to query DB instances according to search criteria.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances?id={id}&name={name}&type={type}&datastore_type={datastore_type}&vpc_id={vpc_id}&subnet_id={subnet_id}&offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                                                                                                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================================================================================================================================================+
      | project_id      | String          | Yes             | Specifies the project ID of a tenant in a region.                                                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                                                                                                                                      |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id              | String          | No              | Specifies the DB instance ID.                                                                                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The asterisk (``*``) is reserved for the system. If the instance ID starts with \*, it indicates that fuzzy match is performed based on the value following \* Otherwise, the exact match is performed based on the instance ID. The value cannot contain only asterisks (``*``).     |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | String          | No              | Specifies the DB instance name.                                                                                                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The asterisk (``*``) is reserved for the system. If the instance name starts with \*, it indicates that fuzzy match is performed based on the value following \* Otherwise, the exact match is performed based on the instance name. The value cannot contain only asterisks (``*``). |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type            | String          | No              | Specifies the instance type based query. The value is **Single**, **Ha**, or **Replica**, which correspond to single instance, primary/standby instances, and read replica, respectively.                                                                                             |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_type  | String          | No              | Specifies the database type. Its value can be any of the following and is case-sensitive:                                                                                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  MySQL                                                                                                                                                                                                                                                                              |
      |                 |                 |                 | -  PostgreSQL                                                                                                                                                                                                                                                                         |
      |                 |                 |                 | -  SQLServer                                                                                                                                                                                                                                                                          |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id          | String          | No              | Specifies the VPC ID.                                                                                                                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  Method 1: Log in to VPC console and view the VPC ID in the VPC details.                                                                                                                                                                                                            |
      |                 |                 |                 | -  Method 2: See the "Querying VPCs" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                                                            |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id       | String          | No              | Specifies the network ID of the subnet.                                                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the network ID on the displayed page.                                                                                                                                            |
      |                 |                 |                 | -  Method 2: See the "Querying Subnets" section under "APIs" or the "Querying Networks" section under "OpenStack Neutron APIs" in *Virtual Private Cloud API Reference*.                                                                                                              |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | Integer         | No              | Specifies the index position. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value must be a positive number.                                   |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | Integer         | No              | Specifies the number of records to be queried. The default value is **100**. The value cannot be a negative number. The minimum value is **1** and the maximum value is **100**.                                                                                                      |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   -  Querying all DB instances

      GET https://rds.eu-de.otc.t-systems.com/v3/97b026aa9cc4417888c14c84a1ad9860/instances

   -  Querying DB instances based on search criteria

      GET https://rds.eu-de.otc.t-systems.com/v3/97b026aa9cc4417888c14c84a1ad9860/instances?id=ed7cc6166ec24360a5ed5c5c9c2ed726in01&name=hy&type=Ha&datastore_type=MySQL&vpc_id=19e5d45d-70fd-4a91-87e9-b27e71c9891f&subnet_id=bd51fb45-2dcb-4296-8783-8623bfe89bb7&offset=0&limit=10&tags=rds001=001,rds002=002

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | instances             | Array of objects      | Indicates the DB instance information.                             |
      |                       |                       |                                                                    |
      |                       |                       | For details, see :ref:`Table 3 <rds_01_0004__table2058713718267>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | total_count           | Integer               | Indicates the total number of resources.                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

   .. _rds_01_0004__table2058713718267:

   .. table:: **Table 3** instances field data structure description

      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                        | Type                  | Description                                                                                                                                                                                                                                              |
      +=============================+=======================+==========================================================================================================================================================================================================================================================+
      | id                          | String                | Indicates the DB instance ID.                                                                                                                                                                                                                            |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                        | String                | Indicates the created DB instance name.                                                                                                                                                                                                                  |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                      | String                | Indicates the DB instance status.                                                                                                                                                                                                                        |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | Value:                                                                                                                                                                                                                                                   |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **BUILD**, the instance is being created.                                                                                                                                                                                                |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **CREATE FAIL**, the instance failed to be created.                                                                                                                                                                                      |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **ACTIVE**, the instance is normal.                                                                                                                                                                                                      |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **FAILED**, the instance is abnormal.                                                                                                                                                                                                    |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **MODIFYING**, the instance is being scaled up.                                                                                                                                                                                          |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **REBOOTING**, the instance is being rebooted.                                                                                                                                                                                           |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **RESTORING**, the instance is being restored.                                                                                                                                                                                           |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **MODIFYING INSTANCE TYPE**, the instance is changing from primary to standby.                                                                                                                                                           |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **SWITCHOVER**, the primary/standby switchover is being performed.                                                                                                                                                                       |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **MIGRATING**, the instance is being migrated.                                                                                                                                                                                           |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **BACKING UP**, the instance is being backed up.                                                                                                                                                                                         |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **MODIFYING DATABASE PORT**, the database port is being changed.                                                                                                                                                                         |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If the value is **SHUTDOWN**, the DB instance is stopped.                                                                                                                                                                                                |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | alias                       | String                | Indicates the DB instance alias.                                                                                                                                                                                                                         |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | private_ips                 | List<String>          | Indicates the private IP address list. It is a blank string until an ECS is created.                                                                                                                                                                     |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_ips                  | List<String>          | Indicates the public IP address list.                                                                                                                                                                                                                    |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | private_dns_names           | List<String>          | Indicates the private domain name list of the DB instance. After a DB instance is created, you need to manually apply for a private domain name, or the private domain name is left blank.                                                               |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_dns_names            | List<String>          | Indicates the public domain name list of the DB instance. Currently, only RDS for SQL Server supports public domain names. After a DB instance is created, you need to manually apply for a public domain name, or the public domain name is left blank. |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port                        | Integer               | Indicates the database port number.                                                                                                                                                                                                                      |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | -  The MySQL database port ranges from 1024 to 65535 (excluding 12017 and 33071, which are occupied by the RDS system and cannot be used).                                                                                                               |
      |                             |                       | -  The PostgreSQL database port ranges from 2100 to 9500.                                                                                                                                                                                                |
      |                             |                       | -  The Microsoft SQL Server database port is 1433 or ranges from 2100 to 9500 (excluding 5355 and 5985).                                                                                                                                                 |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | If this parameter is not set, the default value is as follows:                                                                                                                                                                                           |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | -  For MySQL, the default value is **3306**.                                                                                                                                                                                                             |
      |                             |                       | -  For PostgreSQL, the default value is **5432**.                                                                                                                                                                                                        |
      |                             |                       | -  For Microsoft SQL Server, the default value is **1433**.                                                                                                                                                                                              |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enable_ssl                  | Boolean               | Indicates whether SSL is enabled for the instance.                                                                                                                                                                                                       |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | -  **true**: SSL is enabled for the instance.                                                                                                                                                                                                            |
      |                             |                       | -  **false**: SSL is disabled for the instance.                                                                                                                                                                                                          |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                        | String                | The value is **Single**, **Ha**, or **Replica**, which correspond to single instance, primary/standby instances, and read replica, respectively.                                                                                                         |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ha                          | Object                | Indicates the primary/standby DB instance information. Returned only when you obtain a primary/standby DB instance list.                                                                                                                                 |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | For details, see :ref:`Table 4 <rds_01_0004__table7736377269>`.                                                                                                                                                                                          |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                      | String                | Indicates the region where the DB instance is deployed.                                                                                                                                                                                                  |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore                   | Object                | Indicates the database information.                                                                                                                                                                                                                      |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | For details, see :ref:`Table 5 <rds_01_0004__table187591675262>`.                                                                                                                                                                                        |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created                     | String                | Indicates the creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                                                        |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                                                       |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | The value is empty when the DB instance is being created. After the DB instance is created, the value is not empty.                                                                                                                                      |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | updated                     | String                | Indicates the update time. The format is the same as that of the **created** field.                                                                                                                                                                      |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | The value is empty when the DB instance is being created. After the DB instance is created, the value is not empty.                                                                                                                                      |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | db_user_name                | String                | Indicates the default username.                                                                                                                                                                                                                          |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                      | String                | Indicates the VPC ID.                                                                                                                                                                                                                                    |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id                   | String                | Indicates the network ID of the subnet.                                                                                                                                                                                                                  |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id           | String                | Indicates the security group ID.                                                                                                                                                                                                                         |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | cpu                         | String                | Indicates the number of CPUs. For example, the value **1** indicates 1 vCPU.                                                                                                                                                                             |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mem                         | String                | Indicates the memory size in GB.                                                                                                                                                                                                                         |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor_ref                  | String                | Indicates the specification code.                                                                                                                                                                                                                        |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume                      | Object                | Indicates the volume information.                                                                                                                                                                                                                        |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | For details, see :ref:`Table 6 <rds_01_0004__table14771167122611>`.                                                                                                                                                                                      |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | switch_strategy             | String                | Indicates the database switchover policy. The value can be **reliability** or **availability**, indicating the reliability first and availability first, respectively.                                                                                   |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | read_only_by_user           | Boolean               | Indicates the read-only status of the DB instance. This parameter is available only to RDS for MySQL.                                                                                                                                                    |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | -  **true**: indicates that the DB instance is set to read-only.                                                                                                                                                                                         |
      |                             |                       | -  **false**: indicates that the DB instance is set to read/write.                                                                                                                                                                                       |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy             | Object                | Indicates the backup policy.                                                                                                                                                                                                                             |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | For details, see :ref:`Table 7 <rds_01_0004__table578797132615>`.                                                                                                                                                                                        |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | maintenance_window          | String                | Indicates the start time of the maintenance time window in the UTC format.                                                                                                                                                                               |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | nodes                       | Array of objects      | Indicates the primary/standby DB instance information.                                                                                                                                                                                                   |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | For details, see :ref:`Table 8 <rds_01_0004__table1179987152611>`.                                                                                                                                                                                       |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | related_instance            | Array of objects      | Indicates the list of associated DB instances.                                                                                                                                                                                                           |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | For details, see :ref:`Table 9 <rds_01_0004__table15816167142613>`.                                                                                                                                                                                      |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id          | String                | Indicates the disk encryption key ID.                                                                                                                                                                                                                    |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id       | String                | Indicates the enterprise project ID.                                                                                                                                                                                                                     |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | time_zone                   | String                | Indicates the time zone.                                                                                                                                                                                                                                 |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | charge_info                 | Object                | Indicates the billing information, which is pay-per-use.                                                                                                                                                                                                 |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | For details, see :ref:`Table 10 <rds_01_0004__table992615211258>`.                                                                                                                                                                                       |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                        | Array of objects      | Indicates the tag list. If there is no tag in the list, an empty array is returned.                                                                                                                                                                      |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | For details, see :ref:`Table 11 <rds_01_0004__table10618123761215>`.                                                                                                                                                                                     |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | private_read_only_ips       | List<String>          | Indicates the private IP address list of read replica node.                                                                                                                                                                                              |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | This field is returned only for RDS for MySQL cluster instances.                                                                                                                                                                                         |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | private_read_only_dns_names | List<String>          | Indicates the private domain name list of read replica node.                                                                                                                                                                                             |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | This field is returned only for RDS for MySQL cluster instances.                                                                                                                                                                                         |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | collation                   | String                | Indicates the SQL Server character set list.                                                                                                                                                                                                             |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | This field is returned only for RDS for SQL Server instances.                                                                                                                                                                                            |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_used_space           | Double                | Indicates the backup space usage in GB.                                                                                                                                                                                                                  |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | This field is returned only when you query information about a specified RDS for PostgreSQL or RDS for SQL Server DB instance.                                                                                                                           |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | storage_used_space          | Double                | Indicates the storage space usage in GB.                                                                                                                                                                                                                 |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | This field is returned only when you query information about a specified RDS for PostgreSQL or RDS for SQL Server DB instance.                                                                                                                           |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | order_id                    | String                | Indicates the order ID.                                                                                                                                                                                                                                  |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | max_iops                    | Long                  | Indicates the maximum disk IOPS of the instance.                                                                                                                                                                                                         |
      |                             |                       |                                                                                                                                                                                                                                                          |
      |                             |                       | This field is returned only for RDS for SQL Server instances.                                                                                                                                                                                            |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | associated_with_ddm         | Boolean               | Indicates whether a DDM instance has been associated.                                                                                                                                                                                                    |
      +-----------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0004__table7736377269:

   .. table:: **Table 4** ha field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                         |
      +=======================+=======================+=====================================================================+
      | replication_mode      | String                | Indicates the replication mode for the standby DB instance.         |
      |                       |                       |                                                                     |
      |                       |                       | The value cannot be empty.                                          |
      |                       |                       |                                                                     |
      |                       |                       | -  For MySQL, the value is **async** or **semisync**.               |
      |                       |                       | -  For PostgreSQL, the value is **async** or **sync**.              |
      |                       |                       | -  For Microsoft SQL Server, the value is **sync**.                 |
      |                       |                       |                                                                     |
      |                       |                       | .. note::                                                           |
      |                       |                       |                                                                     |
      |                       |                       |    -  **async** indicates the asynchronous replication mode.        |
      |                       |                       |    -  **semisync** indicates the semi-synchronous replication mode. |
      |                       |                       |    -  **sync** indicates the synchronous replication mode.          |
      +-----------------------+-----------------------+---------------------------------------------------------------------+

   .. _rds_01_0004__table187591675262:

   .. table:: **Table 5** datastore field data structure description

      +------------------+--------+--------------------------------------------------------------------------------------------------------------------+
      | Name             | Type   | Description                                                                                                        |
      +==================+========+====================================================================================================================+
      | type             | String | Indicates the DB engine.                                                                                           |
      +------------------+--------+--------------------------------------------------------------------------------------------------------------------+
      | version          | String | Indicates the database version.                                                                                    |
      +------------------+--------+--------------------------------------------------------------------------------------------------------------------+
      | complete_version | String | Indicates the complete version number. This parameter is returned only when the DB engine is MySQL and PostgreSQL. |
      +------------------+--------+--------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0004__table14771167122611:

   .. table:: **Table 6** volume field data structure description

      ==== ======= ==========================
      Name Type    Description
      ==== ======= ==========================
      type String  Indicates the volume type.
      size Integer Indicates the volume size.
      ==== ======= ==========================

   .. _rds_01_0004__table578797132615:

   .. table:: **Table 7** backup_strategy field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================================================================================================================+
      | start_time            | String                | Indicates the backup time window. Automated backups will be triggered during the backup time window.                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                                                                               |
      |                       |                       | The time is in the UTC format.                                                                                                                                                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | keep_days             | Integer               | Indicates the number of days to retain the generated backup files.                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                               |
      |                       |                       | The value range is from 0 to 732. If the value is **0**, the automated backup policy is not configured or has been disabled. To extend the retention period, contact customer service. Automated backups can be retained for up to 2562 days. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0004__table1179987152611:

   .. table:: **Table 8** nodes field data structure description

      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name              | Type   | Description                                                                                                                                                          |
      +===================+========+======================================================================================================================================================================+
      | id                | String | Indicates the node ID.                                                                                                                                               |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name              | String | Indicates the node name.                                                                                                                                             |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | role              | String | Indicates the node type. The value can be **master**, **slave**, or **readreplica**, indicating the primary node, standby node, and read replica node, respectively. |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status            | String | Indicates the node status.                                                                                                                                           |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone | String | Indicates the AZ.                                                                                                                                                    |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_01_0004__table15816167142613:

   .. table:: **Table 9** related_instance field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------+
      | Name                  | Type                  | Description                                           |
      +=======================+=======================+=======================================================+
      | id                    | String                | Indicates the associated DB instance ID.              |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | type                  | String                | Indicates the associated DB instance type.            |
      |                       |                       |                                                       |
      |                       |                       | -  **replica_of**: indicates the primary DB instance. |
      |                       |                       | -  **replica**: indicates read replicas.              |
      +-----------------------+-----------------------+-------------------------------------------------------+

   .. _rds_01_0004__table992615211258:

   .. table:: **Table 10** chargeInfo field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                    |
      +=================+=================+=================+================================================================+
      | charge_mode     | Yes             | String          | Indicates the billing mode.                                    |
      |                 |                 |                 |                                                                |
      |                 |                 |                 | The value **postPaid** indicates the pay-per-use billing mode. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------+

   .. _rds_01_0004__table10618123761215:

   .. table:: **Table 11** tags field data structure description

      ===== ====== ========================
      Name  Type   Description
      ===== ====== ========================
      key   String Indicates the tag key.
      value String Indicates the tag value.
      ===== ====== ========================

-  Example normal response

   Query DB instances based on specified conditions.

   .. code-block:: text

      {
          "instances": [{
              "id": "ed7cc6166ec24360a5ed5c5c9c2ed726in01",
              "status": "ACTIVE",
              "name": "mysql-0820-022709-01",
              "port": 3306,
              "type": "Single",
              "region": "eu-de",
              "datastore": {
                  "type": "MySQL",
                  "version": "5.7"
              },
              "created": "2018-08-20T02:33:49+0800",
              "updated": "2018-08-20T02:33:50+0800",
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "nodes": [{
                  "id": "06f1c2ad57604ae89e153e4d27f4e4b8no01",
                  "name": "mysql-0820-022709-01_node0",
                  "role": "master",
                  "status": "ACTIVE",
                  "availability_zone": "eu-de-01"
              }],
                      "tags": [],
              "private_ips": ["192.168.0.142"],
                      "private_dns_names": [],
                      "public_dns_names": [],
              "public_ips": ["10.154.219.187", "10.154.219.186"],
              "db_user_name": "root",
                      "enable_ssl": false,
              "vpc_id": "b21630c1-e7d3-450d-907d-39ef5f445ae7",
              "subnet_id": "45557a98-9e17-4600-8aec-999150bc4eef",
              "security_group_id": "38815c5c-482b-450a-80b6-0a301f2afd97",
              "flavor_ref": "rds.mysql.n1.large",
              "switch_strategy": "",
              "backup_strategy": {
                  "start_time": "19:00-20:00",
                  "keep_days": 7
              },
              "maintenance_window": "02:00-06:00",
              "related_instance": [],
              "disk_encryption_id": "",
              "time_zone": ""
          }],
          "total_count": 1
      }

-  Query all DB instances.

   .. code-block:: text

      {
          "instances": [{
              "id": "ed7cc6166ec24360a5ed5c5c9c2ed726in01",
              "status": "ACTIVE",
              "name": "mysql-0820-022709-01",
              "port": 3306,
              "type": "Single",
              "region": "eu-de",
              "datastore": {
                  "type": "MySQL",
                  "version": "5.7"
              },
              "created": "2018-08-20T02:33:49+0800",
              "updated": "2018-08-20T02:33:50+0800",
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "nodes": [{
                  "id": "06f1c2ad57604ae89e153e4d27f4e4b8no01",
                  "name": "mysql-0820-022709-01_node0",
                  "role": "master",
                  "status": "ACTIVE",
                  "availability_zone": "eu-de-01"
              }],
              "private_ips": ["192.168.0.142"],
              "public_ips": ["10.154.219.187", "10.154.219.186"],
              "db_user_name": "root",
              "vpc_id": "b21630c1-e7d3-450d-907d-39ef5f445ae7",
              "subnet_id": "45557a98-9e17-4600-8aec-999150bc4eef",
              "security_group_id": "38815c5c-482b-450a-80b6-0a301f2afd97",
              "flavor_ref": "rds.mysql.n1.large",
              "switch_strategy": "",
              "backup_strategy": {
                  "start_time": "19:00-20:00",
                  "keep_days": 7
              },
              "maintenance_window": "02:00-06:00",
              "related_instance": [],
              "disk_encryption_id": "",
              "time_zone": ""
          }, {
              "id": "ed7cc6166ec24360a5ed5c5c9c2ed726in02",
              "status": "ACTIVE",
              "name": "mysql-0820-022709-02",
              "port": 3306,
              "type": "Single",
              "region": "eu-de",
              "datastore": {
                  "type": "MySQL",
                  "version": "5.7"
              },
              "created": "2019-08-20T02:33:49+0800",
              "updated": "2019-08-20T02:33:50+0800",
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "nodes": [{
                  "id": "06f1c2ad57604ae89e153e4d27f4e4b8no01",
                  "name": "mysql-0820-022709-01_node0",
                  "role": "master",
                  "status": "ACTIVE",
                  "availability_zone": "eu-de-01"
              }],
              "private_ips": ["192.168.0.142"],
              "public_ips": ["10.154.219.187", "10.154.219.186"],
              "db_user_name": "root",
              "vpc_id": "b21630c1-e7d3-450d-907d-39ef5f445ae7",
              "subnet_id": "45557a98-9e17-4600-8aec-999150bc4eef",
              "security_group_id": "38815c5c-482b-450a-80b6-0a301f2afd97",
              "flavor_ref": "rds.mysql.n1.large",
              "switch_strategy": "",
              "backup_strategy": {
                  "start_time": "19:00-20:00",
                  "keep_days": 7
              },
              "maintenance_window": "02:00-06:00",
              "related_instance": [],
              "disk_encryption_id": "",
              "time_zone": ""
          }],
          "total_count": 2
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
