:original_name: rds_09_0008.html

.. _rds_09_0008:

Restoring Data to a New DB Instance
===================================

Function
--------

This API is used to restore data to a new DB instance (v3).

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The DB engine of the original DB instance must be the same as that of the target DB instance. For example, if the original DB instance is running MySQL, the target DB instance must also run MySQL.
-  All DB engine versions of the original and new DB instances must be consistent.
-  The total volume size of the new DB instance must be greater than or equal to that of the original DB instance.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name               | Mandatory       | Type            | Description                                                                                                                                                                                                                                          |
      +====================+=================+=================+======================================================================================================================================================================================================================================================+
      | name               | Yes             | String          | Specifies the DB instance name.                                                                                                                                                                                                                      |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | DB instances of the same type can have same names under the same tenant.                                                                                                                                                                             |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | The value must be 4 to 64 characters in length and start with a letter. It is case-insensitive and can contain only letters, digits, hyphens (-), and underscores (_).                                                                               |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ha                 | No              | Object          | Specifies the HA configuration parameters, which are used when creating primary/standby DB instances.                                                                                                                                                |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | For details, see :ref:`Table 3 <rds_09_0008__table13260175614296>`.                                                                                                                                                                                  |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | configuration_id   | No              | String          | Specifies the parameter template ID.                                                                                                                                                                                                                 |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port               | No              | String          | Specifies the database port information.                                                                                                                                                                                                             |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | -  The MySQL database port ranges from 1024 to 65535 (excluding 12017 and 33071, which are occupied by the RDS system and cannot be used).                                                                                                           |
      |                    |                 |                 | -  The PostgreSQL database port ranges from 2100 to 9500.                                                                                                                                                                                            |
      |                    |                 |                 | -  The Microsoft SQL Server database port is 1433 or ranges from 2100 to 9500 (excluding 5355 and 5985).                                                                                                                                             |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | If this parameter is not set, the default value is as follows:                                                                                                                                                                                       |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | -  For MySQL, the default value is **3306**.                                                                                                                                                                                                         |
      |                    |                 |                 | -  For PostgreSQL, the default value is **5432**.                                                                                                                                                                                                    |
      |                    |                 |                 | -  For Microsoft SQL Server, the default value is **1433**.                                                                                                                                                                                          |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | password           | Yes             | String          | Specifies the database password.                                                                                                                                                                                                                     |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | Valid value:                                                                                                                                                                                                                                         |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | A database password must be 8 to 32 characters long and contain at least three types of the following characters: uppercase letters, lowercase letters, digits, and special characters.                                                              |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | Different DB engines support different special characters.                                                                                                                                                                                           |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | -  RDS for MySQL:``~!@#$%^*-_=+?,()&``                                                                                                                                                                                                               |
      |                    |                 |                 | -  RDS for PostgreSQL:``~!@#$%^*-_=+?,``                                                                                                                                                                                                             |
      |                    |                 |                 | -  RDS for SQL Server:``~!@#$%^*-_+?,``                                                                                                                                                                                                              |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | You are advised to enter a strong password to improve security, preventing security risks such as brute force cracking. If the password you provide is regarded as a weak password by the system, you will be prompted to enter a stronger password. |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy    | No              | Object          | Specifies the advanced backup policy.                                                                                                                                                                                                                |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | For details, see :ref:`Table 4 <rds_09_0008__table0863181193416>`.                                                                                                                                                                                   |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id | No              | String          | Specifies the key ID for disk encryption. The default value is empty.                                                                                                                                                                                |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor_ref         | Yes             | String          | Specifies the specification code. The value cannot be empty.                                                                                                                                                                                         |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | For details, see **spec_code** in section :ref:`Querying Database Specifications <rds_06_0002>`.                                                                                                                                                     |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume             | Yes             | Object          | Specifies the volume information.                                                                                                                                                                                                                    |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | For details, see :ref:`Table 5 <rds_09_0008__table10656503>`.                                                                                                                                                                                        |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone  | Yes             | String          | Specifies the AZ ID. If the DB instance is not a single instance, you need to specify an AZ for each node of the instance and separate the AZs with commas (,). For details, see the example.                                                        |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | The value cannot be empty. For details about how to obtain this parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                                                                           |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id             | Yes             | String          | Specifies the VPC ID. To obtain this parameter value, use either of the following methods:                                                                                                                                                           |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | -  Method 1: Log in to VPC console and view the VPC ID in the VPC details.                                                                                                                                                                           |
      |                    |                 |                 | -  Method 2: See the "Querying VPCs" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                           |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id          | Yes             | String          | Specifies the network ID. To obtain this parameter value, use either of the following methods:                                                                                                                                                       |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the network ID on the displayed page.                                                                                                           |
      |                    |                 |                 | -  Method 2: See the "Querying Subnets" section under "APIs" or the "Querying Networks" section under "OpenStack Neutron APIs" in *Virtual Private Cloud API Reference*.                                                                             |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | data_vip           | No              | String          | Specifies the floating IP address of a DB instance. To obtain this parameter value, use either of the following methods:                                                                                                                             |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the subnet CIDR block on the displayed page.                                                                                                    |
      |                    |                 |                 | -  Method 2: See the "Querying Subnets" section under "APIs" in the *Virtual Private Cloud API Reference*.                                                                                                                                           |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id  | No              | String          | Specifies the security group which the RDS DB instance belongs to. To obtain this parameter value, use either of the following methods:                                                                                                              |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | -  Method 1: Log in to VPC console. Choose **Access Control** > **Security Groups** in the navigation pane on the left. On the displayed page, click the target security group. You can view the security group ID on the displayed page.            |
      |                    |                 |                 | -  Method 2: See the "Querying Security Groups" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restore_point      | Yes             | Object          | Specifies the restoration information.                                                                                                                                                                                                               |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | For details, see :ref:`Table 6 <rds_09_0008__table15343138128>`.                                                                                                                                                                                     |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | collation          | No              | String          | This parameter applies only to Microsoft SQL Server DB instances.                                                                                                                                                                                    |
      |                    |                 |                 |                                                                                                                                                                                                                                                      |
      |                    |                 |                 | Value range: character sets queried in :ref:`Querying the Available SQL Server Character Set <rds_05_0010>`.                                                                                                                                         |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0008__table13260175614296:

   .. table:: **Table 3** ha field data structure description

      +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
      | Name             | Mandatory       | Type            | Description                                                                                                            |
      +==================+=================+=================+========================================================================================================================+
      | mode             | Yes             | String          | Specifies the DB instance type. The value is **Ha** (Primary/Standby or Cluster DB instances) and is case-insensitive. |
      +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
      | replication_mode | Yes             | String          | Specifies the replication mode for the standby DB instance.                                                            |
      |                  |                 |                 |                                                                                                                        |
      |                  |                 |                 | The value cannot be empty.                                                                                             |
      |                  |                 |                 |                                                                                                                        |
      |                  |                 |                 | -  For MySQL, the value is **async** or **semisync**.                                                                  |
      |                  |                 |                 | -  For PostgreSQL, the value is **async** or **sync**.                                                                 |
      |                  |                 |                 | -  For Microsoft SQL Server, the value is **sync**.                                                                    |
      |                  |                 |                 |                                                                                                                        |
      |                  |                 |                 | .. note::                                                                                                              |
      |                  |                 |                 |                                                                                                                        |
      |                  |                 |                 |    -  **async** indicates the asynchronous replication mode.                                                           |
      |                  |                 |                 |    -  **semisync** indicates the semi-synchronous replication mode.                                                    |
      |                  |                 |                 |    -  **sync** indicates the synchronous replication mode.                                                             |
      +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0008__table0863181193416:

   .. table:: **Table 4** backup_strategy field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================================================================================================+
      | start_time      | Yes             | String          | Specifies the backup time window. Automated backups will be triggered during the backup time window.                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | The value cannot be empty. It must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                                                                                                                    |
      |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to any of the following: **00**, **15**, **30**, or **45**.                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | Example value:                                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | -  08:15-09:15                                                                                                                                                                                                                                  |
      |                 |                 |                 | -  23:00-00:00                                                                                                                                                                                                                                  |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | keep_days       | No              | Integer         | Specifies the retention days for specific backup files.                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | The value range is from 0 to 732. If this parameter is not specified or set to **0**, the automated backup policy is disabled. To extend the retention period, contact customer service. Automated backups can be retained for up to 2562 days. |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | .. note::                                                                                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 |    For SQL Server Primary/Standby and Cluster instance parameter "keep_days" cannot be set to 0.                                                                                                                                                |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0008__table10656503:

   .. table:: **Table 5** volume field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                            |
      +=================+=================+=================+========================================================================================================================================================================================+
      | type            | Yes             | String          | Specifies the volume type.                                                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                        |
      |                 |                 |                 | Its value can be any of the following and is case-sensitive:                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                                                        |
      |                 |                 |                 | -  **COMMON**: SATA storage.                                                                                                                                                           |
      |                 |                 |                 | -  **ULTRAHIGH**: ultra-high I/O storage.                                                                                                                                              |
      |                 |                 |                 | -  **CLOUDSSD**: cloud SSD storage.                                                                                                                                                    |
      |                 |                 |                 | -  **ESSD**: extreme SSD storage.                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                        |
      |                 |                 |                 | .. note::                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                        |
      |                 |                 |                 |    -  The MySQL and PostgreSQL DB engines support the following volume types: **CLOUDSSD** and **ESSD**. **ESSD** is not supported for Single instance types for MySQL and PostgreSQL. |
      |                 |                 |                 |    -  The SQL Server engine supports the following volume types: **COMMON**, **ULTRAHIGH**, and **ESSD**.                                                                              |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | Yes             | Integer         | Specifies the volume size.                                                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                        |
      |                 |                 |                 | Its value range is from 40 GB to 4000 GB. The value must be a multiple of 10.                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                        |
      |                 |                 |                 | .. important::                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                        |
      |                 |                 |                 |    NOTICE:                                                                                                                                                                             |
      |                 |                 |                 |    The volume size of the new DB instance must be greater than or equal to that of the original DB instance.                                                                           |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0008__table15343138128:

   .. table:: **Table 6** restore_point field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================+
      | instance_id     | Yes             | String          | Specifies the DB instance ID.                                                                                                       |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | type            | No              | String          | Specifies the restoration mode. Enumerated values include                                                                           |
      |                 |                 |                 |                                                                                                                                     |
      |                 |                 |                 | -  **backup**: indicates restoration from backup files. In this mode, **backup_id** is mandatory when **type** is not mandatory.    |
      |                 |                 |                 | -  **timestamp**: indicates point-in-time restoration. In this mode, **restore_time** is mandatory when **type** is mandatory.      |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | backup_id       | No              | String          | Specifies the ID of the backup used to restore data. This parameter must be specified when the backup file is used for restoration. |
      |                 |                 |                 |                                                                                                                                     |
      |                 |                 |                 | .. important::                                                                                                                      |
      |                 |                 |                 |                                                                                                                                     |
      |                 |                 |                 |    NOTICE:                                                                                                                          |
      |                 |                 |                 |    When **type** is **backup**, **backup_id** is mandatory.                                                                         |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | restore_time    | No              | Integer         | Specifies the time point of data restoration in the UNIX timestamp. The unit is millisecond and the time zone is UTC.               |
      |                 |                 |                 |                                                                                                                                     |
      |                 |                 |                 | .. important::                                                                                                                      |
      |                 |                 |                 |                                                                                                                                     |
      |                 |                 |                 |    NOTICE:                                                                                                                          |
      |                 |                 |                 |    When **type** is **timestamp**, **restore_time** is mandatory.                                                                   |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances

-  Request example

   Use backup files for restoration:

   .. code-block:: text

      {
          "name": "targetInst",
          "availability_zone": "eu-de-01,eu-de-02",
          "ha": {
              "mode": "ha",
              "replication_mode": "async"
          },
          "flavor_ref": "rds.mysql.n1.large",
          "volume": {
              "type": "ULTRAHIGH",
              "size": 40
          },
          "disk_encryption_id": "2gfdsh-844a-4023-a776-fc5c5fb71fb4",
          "vpc_id": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
          "subnet_id": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f",
          "security_group_id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5",
          "backup_strategy": {
              "keep_days": 2,
              "start_time": "19:00-20:00"
          },
          "password": "Demo@12345678",
          "configuration_id": "52e86e87445847a79bf807ceda213165pr01",
          "restore_point": {
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin01",
              "type": "backup",
              "backup_id": "2f4ddb93-b901-4b08-93d8-1d2e472f30fe"
          }
      }

   Use PITR for restoration:

   .. code-block:: text

      {
          "name": "targetInst",
          "availability_zone": "eu-de-01,eu-de-02",
          "ha": {
              "mode": "ha",
              "replication_mode": "async"
          },
          "flavor_ref": "rds.mysql.n1.large",
          "volume": {
              "type": "ULTRAHIGH",
              "size": 40
          },
          "disk_encryption_id": "2gfdsh-844a-4023-a776-fc5c5fb71fb4",
          "vpc_id": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
          "subnet_id": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f",
          "security_group_id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5",
          "backup_strategy": {
              "keep_days": 2,
              "start_time": "19:00-20:00"
          },
          "password": "Demo@12345678",
          "configuration_id": "52e86e87445847a79bf807ceda213165pr01",
          "restore_point": {
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin01",
              "type": "timestamp",
              "restore_time": 1532001446987
          }
      }

Response
--------

-  Normal response

   .. table:: **Table 7** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                       |
      +=======================+=======================+===================================================================+
      | instance              | Object                | Indicates the DB instance information.                            |
      |                       |                       |                                                                   |
      |                       |                       | For details, see :ref:`Table 8 <rds_09_0008__table175305610274>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | job_id                | String                | Indicates the ID of the DB instance creation task.                |
      +-----------------------+-----------------------+-------------------------------------------------------------------+

   .. _rds_09_0008__table175305610274:

   .. table:: **Table 8** instance description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                                               |
      +=======================+=======================+===========================================================================================================================================================================================================================================+
      | id                    | String                | Indicates the DB instance ID.                                                                                                                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the DB instance name.                                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | DB instances of the same type can have same names under the same tenant.                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | The value must be 4 to 64 characters in length and start with a letter. It is case-insensitive and can contain only letters, digits, hyphens (-), and underscores (_).                                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the DB instance status. For example, **BUILD** indicates that the DB instance is being created.                                                                                                                                 |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore             | Object                | Indicates the database information.                                                                                                                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 9 <rds_09_0008__table766045720277>`.                                                                                                                                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ha                    | Object                | Indicates the HA configuration parameters. This parameter is returned only when primary/standby DB instances are created.                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 10 <rds_09_0008__table15899105722713>`.                                                                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | configuration_id      | String                | Indicates the parameter template ID. This parameter is returned only when a custom parameter template is used during DB instance creation.                                                                                                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port                  | String                | Indicates the database port information.                                                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  The MySQL database port ranges from 1024 to 65535 (excluding 12017 and 33071, which are occupied by the RDS system and cannot be used).                                                                                                |
      |                       |                       | -  The PostgreSQL database port ranges from 2100 to 9500.                                                                                                                                                                                 |
      |                       |                       | -  The Microsoft SQL Server database port is 1433 or ranges from 2100 to 9500 (excluding 5355 and 5985).                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | If this parameter is not set, the default value is as follows:                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  For MySQL, the default value is **3306**.                                                                                                                                                                                              |
      |                       |                       | -  For PostgreSQL, the default value is **5432**.                                                                                                                                                                                         |
      |                       |                       | -  For Microsoft SQL Server, the default value is **1433**.                                                                                                                                                                               |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | Object                | Indicates the automated backup policy.                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 11 <rds_09_0008__table81249589270>`.                                                                                                                                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor_ref            | String                | Indicates the specification ID.                                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see **spec_code** in :ref:`Table 3 <rds_06_0002__table1336414511696>` in section :ref:`Querying Database Specifications <rds_06_0002>`.                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume                | Object                | Indicates the volume information.                                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | For details, see :ref:`Table 12 <rds_09_0008__table5324165817272>`.                                                                                                                                                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | String                | Indicates the region ID.                                                                                                                                                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone     | String                | Indicates the AZ ID.                                                                                                                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | String                | Indicates the VPC ID. To obtain this parameter value, use either of the following methods:                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  Method 1: Log in to VPC console and view the VPC ID in the VPC details.                                                                                                                                                                |
      |                       |                       | -  Method 2: See the "Querying VPCs" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | String                | Indicates the network ID. To obtain this parameter value, use either of the following methods:                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the network ID on the displayed page.                                                                                                |
      |                       |                       | -  Method 2: See the "Querying Subnets" section under "APIs" or the "Querying Networks" section under "OpenStack Neutron APIs" in *Virtual Private Cloud API Reference*.                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | String                | Indicates the security group which the RDS DB instance belongs to. To obtain this parameter value, use either of the following methods:                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                           |
      |                       |                       | -  Method 1: Log in to VPC console. Choose **Access Control** > **Security Groups** in the navigation pane on the left. On the displayed page, click the target security group. You can view the security group ID on the displayed page. |
      |                       |                       | -  Method 2: See the "Querying Security Groups" section in the *Virtual Private Cloud API Reference*.                                                                                                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | collation             | String                | Indicates the collation for Microsoft SQL Server.                                                                                                                                                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0008__table766045720277:

   .. table:: **Table 9** datastore field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                          |
      +=================+=================+=================+======================================================================================================================+
      | type            | Yes             | String          | Indicates the DB engine. Its value can be any of the following and is case-insensitive:                              |
      |                 |                 |                 |                                                                                                                      |
      |                 |                 |                 | -  MySQL                                                                                                             |
      |                 |                 |                 | -  PostgreSQL                                                                                                        |
      |                 |                 |                 | -  SQLServer                                                                                                         |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
      | version         | Yes             | String          | Indicates the database version.                                                                                      |
      |                 |                 |                 |                                                                                                                      |
      |                 |                 |                 | For details about supported database versions, see section :ref:`Database Version Queries <en-us_topic_0032347782>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0008__table15899105722713:

   .. table:: **Table 10** ha field data structure description

      +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
      | Name             | Mandatory       | Type            | Description                                                                         |
      +==================+=================+=================+=====================================================================================+
      | mode             | Yes             | String          | Indicates the DB instance type. The value is **Ha** (primary/standby DB instances). |
      +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
      | replication_mode | Yes             | String          | Indicates the replication mode for the standby DB instance.                         |
      |                  |                 |                 |                                                                                     |
      |                  |                 |                 | The value cannot be empty.                                                          |
      |                  |                 |                 |                                                                                     |
      |                  |                 |                 | -  For MySQL, the value is **async** or **semisync**.                               |
      |                  |                 |                 | -  For PostgreSQL, the value is **async** or **sync**.                              |
      |                  |                 |                 | -  For Microsoft SQL Server, the value is **sync**.                                 |
      |                  |                 |                 |                                                                                     |
      |                  |                 |                 | .. note::                                                                           |
      |                  |                 |                 |                                                                                     |
      |                  |                 |                 |    -  **async** indicates the asynchronous replication mode.                        |
      |                  |                 |                 |    -  **semisync** indicates the semi-synchronous replication mode.                 |
      |                  |                 |                 |    -  **sync** indicates the synchronous replication mode.                          |
      +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+

   .. _rds_09_0008__table81249589270:

   .. table:: **Table 11** backupStrategy field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================================================================================================+
      | start_time      | Yes             | String          | Indicates the backup time window. Automated backups will be triggered during the backup time window.                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | The value cannot be empty. It must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                                                                                                                    |
      |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to any of the following: **00**, **15**, **30**, or **45**.                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | Example value:                                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | -  08:15-09:15                                                                                                                                                                                                                                  |
      |                 |                 |                 | -  23:00-00:00                                                                                                                                                                                                                                  |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | keep_days       | No              | Integer         | Indicates the retention days for specific backup files.                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                 |
      |                 |                 |                 | The value range is from 0 to 732. If this parameter is not specified or set to **0**, the automated backup policy is disabled. To extend the retention period, contact customer service. Automated backups can be retained for up to 2562 days. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0008__table5324165817272:

   .. table:: **Table 12** volume field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                   |
      +=================+=================+=================+===============================================================================+
      | type            | Yes             | String          | Indicates the volume type.                                                    |
      |                 |                 |                 |                                                                               |
      |                 |                 |                 | Its value can be any of the following and is case-sensitive:                  |
      |                 |                 |                 |                                                                               |
      |                 |                 |                 | -  **COMMON**: SATA storage.                                                  |
      |                 |                 |                 | -  **ULTRAHIGH**: ultra-high I/O storage.                                     |
      |                 |                 |                 | -  **CLOUDSSD**: cloud SSD storage.                                           |
      |                 |                 |                 | -  **ESSD**: extreme SSD storage.                                             |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
      | size            | Yes             | Integer         | Indicates the volume size.                                                    |
      |                 |                 |                 |                                                                               |
      |                 |                 |                 | Its value range is from 40 GB to 4000 GB. The value must be a multiple of 10. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "instance": {
              "id": "f5ffdd8b1c98434385eb001904209eacin01",
              "name": "demoname",
              "status": "BUILD",
              "datastore": {
                  "type": "MySQL",
                  "version": "5.6.41"
              },
              "port": "3306",
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": "40"
              },
              "region": "eu-de",
              "backup_strategy": {
                  "start_time": "02:00-03:00",
                  "keep_days": "7"
              },
              "flavor_ref": "rds.mysql.n1.large",
              "availability_zone": "eu-de-01",
              "vpc_id": "19e5d45d-70fd-4a91-87e9-b27e71c9891f",
              "subnet_id": "bd51fb45-2dcb-4296-8783-8623bfe89bb7",
              "security_group_id": "23fd0cd4-15dc-4d65-bdb3-8844cc291be0"
          },
          "job_id": "bf003379-afea-4aa5-aa83-4543542070bc"
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

-  Normal

   202

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
