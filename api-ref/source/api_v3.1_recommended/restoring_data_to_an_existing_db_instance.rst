:original_name: rds_07_0003.html

.. _rds_07_0003:

Restoring Data to an Existing DB Instance
=========================================

Function
--------

This API is used to restore a database to an existing DB Instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  When data is restored to an existing DB instance, the API has the following constraints:

   -  The DB engine of the original DB instance must be the same as that of the target DB instance. For example, if the original DB instance is running MySQL, the target DB instance must also run MySQL.
   -  For RDS for MySQL, the DB engine version of the target DB instance must be at least equal to that of the original DB instance, for example, from MySQL 5.7.25 to 5.7.27.
   -  For RDS for PostgreSQL, the DB engine version of the target DB instance must be the same as that of the original DB instance.
   -  For RDS for SQL Server, the time zone of the target DB instance must be the same as that of the original DB instance. Otherwise, data inconsistency may occur.
   -  For version constraints of RDS for SQL Server, see :ref:`Table 1 <rds_07_0003__table23213613434>`.
   -  The total storage space of the target DB instance must be at least equal to that of the original DB instance for RDS for MySQL.
   -  Cross-region restoration is not supported.
   -  For RDS for MySQL DB instances, when data is restored to an existing DB instance, the case sensitivity setting of the existing DB instance must be the same as that of the original DB instance. Otherwise, the restoration may fail.

-  When data is restored to an original DB instance:

   This API is supported only for MySQL and Microsoft SQL Server DB engines.

   .. _rds_07_0003__table23213613434:

   .. table:: **Table 1** Restoring to specific DB engine versions

      +-----------------------------------+-----------------------------------+
      | Original DB Engine Version        | Restore To                        |
      +===================================+===================================+
      | 2017 Standard Edition             | 2017 Standard Edition             |
      |                                   |                                   |
      |                                   | 2017 Enterprise Edition           |
      |                                   |                                   |
      |                                   | 2019 Standard Edition             |
      |                                   |                                   |
      |                                   | 2019 Enterprise Edition           |
      +-----------------------------------+-----------------------------------+
      | 2017 Enterprise Edition           | 2017 Enterprise Edition           |
      |                                   |                                   |
      |                                   | 2019 Enterprise Edition           |
      +-----------------------------------+-----------------------------------+
      | 2019 Standard Edition             | 2019 Standard Edition             |
      |                                   |                                   |
      |                                   | 2019 Enterprise Edition           |
      |                                   |                                   |
      |                                   | 2022 Standard Edition             |
      |                                   |                                   |
      |                                   | 2022 Enterprise Edition           |
      +-----------------------------------+-----------------------------------+
      | 2019 Enterprise Edition           | 2019 Standard Edition             |
      |                                   |                                   |
      |                                   | 2019 Enterprise Edition           |
      |                                   |                                   |
      |                                   | 2022 Enterprise Edition           |
      +-----------------------------------+-----------------------------------+
      | 2022 Standard Edition             | 2022 Standard Edition             |
      |                                   |                                   |
      |                                   | 2022 Enterprise Edition           |
      +-----------------------------------+-----------------------------------+
      | 2022 Enterprise Edition           | 2022 Standard Edition             |
      |                                   |                                   |
      |                                   | 2022 Enterprise Edition           |
      +-----------------------------------+-----------------------------------+

URI
---

-  URI format

   POST https://{*endpoint*}/v3.1/{project_id}/instances/recovery

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | Content-Type    | Yes             | String          | The content type.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The default value is **application/json**.                                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | source          | Yes             | Object          | Restoration information.                                            |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | For details, see :ref:`Table 5 <rds_07_0003__table15343138128>`.    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | target          | Yes             | Object          | Instance to which the backup is restored.                           |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | For details, see :ref:`Table 6 <rds_07_0003__table13185192412159>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

.. _rds_07_0003__table15343138128:

.. table:: **Table 5** source field data structure description

   +----------------------+-----------------+---------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type                | Description                                                                                                                                                                                                       |
   +======================+=================+=====================+===================================================================================================================================================================================================================+
   | instance_id          | Yes             | String              | Instance ID.                                                                                                                                                                                                      |
   +----------------------+-----------------+---------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                 | No              | String              | Restoration mode of the instance. Enumerated values include:                                                                                                                                                      |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | -  **backup**: indicates using backup files for restoration. In this mode, **type** is not mandatory and **backup_id** is mandatory.                                                                              |
   |                      |                 |                     | -  **timestamp**: indicates the point-in-time restoration mode. In this mode, **type** and **restore_time** are mandatory.                                                                                        |
   +----------------------+-----------------+---------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_id            | No              | String              | ID of the backup used to restore data. This parameter must be specified when the backup file is used for restoration.                                                                                             |
   +----------------------+-----------------+---------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | restore_time         | No              | Integer             | Time point of data restoration in the UNIX timestamp format. The unit is millisecond and the time zone is UTC.                                                                                                    |
   +----------------------+-----------------+---------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | database_name        | No              | Map<String, String> | Name of the new database after the restoration. If this parameter is available, you can restore specific databases and rename new databases.                                                                      |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | -  This parameter is only available to RDS for SQL Server.                                                                                                                                                        |
   |                      |                 |                     | -  If this parameter is not specified, all databases are restored by default.                                                                                                                                     |
   |                      |                 |                     | -  Before the restoration, make sure that the size of the restored data does not exceed the purchased disk capacity. Expand disk capacity, if necessary.                                                          |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | -  You can enter multiple new database names and separate them with commas (,). The new database names can contain the original database names.                                                                   |
   |                      |                 |                     | -  New database names must be different from the original database names. If they are left blank, the original database names will be used for restoration by default.                                            |
   |                      |                 |                     | -  Check whether new database names are case sensitive based on the character set selected during instance creation and make sure each new database name is unique.                                               |
   |                      |                 |                     | -  The total number of new and existing databases on the existing or original DB instances where data is restored cannot exceed the database quota specified by **rds_databases_quota**.                          |
   |                      |                 |                     | -  New database names cannot contain the following fields (case-insensitive): rdsadmin, master, msdb, tempdb, model, and resource.                                                                                |
   |                      |                 |                     | -  New database names must consist of 1 to 64 characters, including only letters, digits, underscores (_), and hyphens (-). If you want to restore data to multiple new databases, separate them with commas (,). |
   |                      |                 |                     | -  New database names must be different from any database names on the original DB instance.                                                                                                                      |
   |                      |                 |                     | -  New database names must be different from any database names on the existing or original DB instances where data is restored.                                                                                  |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | Example:                                                                                                                                                                                                          |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | .. code:: text                                                                                                                                                                                                    |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     |    "database_name":{"Original database name":"New database name"}                                                                                                                                                 |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | Correct example: "database_name":{"A":"A,A1,A2","B":"B1,B2","C":""}                                                                                                                                               |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | Wrong example: "database_name":{"A":"A","B":"B1,B2","C":"B1,C1","D":"D1,d1"},                                                                                                                                     |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | Error causes are as follows:                                                                                                                                                                                      |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | -  The new database name (A) is the same as the original database name (A).                                                                                                                                       |
   |                      |                 |                     | -  The new database name (B1) is not unique.                                                                                                                                                                      |
   |                      |                 |                     | -  When the database name is case insensitive, the database names D1 and d1 conflict.                                                                                                                             |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | -  Exercise caution when restoring data to an existing or original DB instance.                                                                                                                                   |
   +----------------------+-----------------+---------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | restore_all_database | No              | Boolean             | Whether to restore all databases to the target instance.                                                                                                                                                          |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | This field is available only for Microsoft SQL Server. Enumerated values include:                                                                                                                                 |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | -  **true**: All databases will be restored to the target instance.                                                                                                                                               |
   |                      |                 |                     | -  **false**: Not all databases will be restored to the target instance.                                                                                                                                          |
   |                      |                 |                     |                                                                                                                                                                                                                   |
   |                      |                 |                     | The default value is **false**.                                                                                                                                                                                   |
   +----------------------+-----------------+---------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _rds_07_0003__table13185192412159:

.. table:: **Table 6** target field data structure description

   +-------------+-----------+--------+---------------------------------------------------------------------------+
   | Name        | Mandatory | Type   | Description                                                               |
   +=============+===========+========+===========================================================================+
   | instance_id | Yes       | String | Specifies the ID of the DB instance where the backup will be restored to. |
   +-------------+-----------+--------+---------------------------------------------------------------------------+

Example Request
---------------

-  Restore data to a DB instance from a backup.

   .. code-block:: text

      POST https://rds.eu-de.otc.t-systems.com/v3.1/0483b6b16e954cb88930a360d2c4e663/instances/recovery

      {
          "source": {
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin01",
              "type": "backup",
              "backup_id": "2f4ddb93-b901-4b08-93d8-1d2e472f30fe"
          },
          "target": {
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin01"
          }
      }

-  Restore all databases to a DB instance from an RDS for SQL Server backup.

   .. code-block::

      {
          "source": {
              "instance_id": "61879e6085bc44d1831b0ce62d988fd9in04",
              "type": "backup",
              "backup_id": "b021670e69ba4538b7b2ed07257306aebr04",
                      "restore_all_database":true
          },
          "target": {
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin04"
          }
      }

-  Restore instance data to a specific point in time.

   .. code-block::

      {
          "source": {
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin01",
              "type": "timestamp",
              "restore_time": 1532001446987
          },
          "target": {
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin01"
          }
      }

-  Restore some databases of an RDS for SQL Server instance to a specific point in time.

   .. code-block::

      {
          "source": {
              "instance_id": "61879e6085bc44d1831b0ce62d988fd9in04",
              "type": "timestamp",
              "restore_time": 1532001446987,
              "database_name": {
                  "db1": "dbtest1",
                              "db3": ""
              }
          },
          "target": {
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin04"
          }
      }

Response
--------

-  Normal response

   .. table:: **Table 7** Parameter description

      ====== ====== =====================
      Name   Type   Description
      ====== ====== =====================
      job_id String Indicates the job ID.
      ====== ====== =====================

-  Example normal response

   .. code-block::

      {
          "job_id": "ff80808157127d9301571bf8160c001d"
      }

-  Abnormal response

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
