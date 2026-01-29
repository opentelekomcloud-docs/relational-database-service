:original_name: rds_09_0009.html

.. _rds_09_0009:

Restoring Data to an Existing or Original DB Instance
=====================================================

Function
--------

This API is used to restore a database to an existing or the original DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  When data is restored to an existing DB instance, the API has the following constraints:

   -  The DB engine of the original DB instance must be the same as that of the target DB instance. For example, if the original DB instance is running MySQL, the target DB instance must also run MySQL.
   -  For RDS for MySQL, the DB engine version of the target DB instance must be at least equal to that of the original DB instance, for example, from MySQL 5.7.25 to 5.7.27.
   -  For RDS for PostgreSQL, the DB engine version of the target DB instance must be the same as that of the original DB instance.
   -  For RDS for SQL Server, the time zone of the target DB instance must be the same as that of the original DB instance. Otherwise, data inconsistency may occur.
   -  For version constraints of RDS for SQL Server, see :ref:`Table 1 <rds_09_0009__table1334944713437>`.
   -  The total storage space of the target DB instance must be at least equal to that of the original DB instance for RDS for MySQL.
   -  Cross-region restoration is not supported.
   -  For RDS for MySQL DB instances, when data is restored to an existing DB instance, the case sensitivity setting of the existing DB instance must be the same as that of the original DB instance. Otherwise, the restoration may fail.

-  When data is restored to an original DB instance:

   This API is supported only for MySQL and Microsoft SQL Server DB engines.

   .. _rds_09_0009__table1334944713437:

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

   POST https://{*Endpoint*}/v3/{project_id}/instances/recovery

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

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                         |
      +=================+=================+=================+=====================================================================+
      | source          | Yes             | Object          | Specifies the restoration information.                              |
      |                 |                 |                 |                                                                     |
      |                 |                 |                 | For details, see :ref:`Table 4 <rds_09_0009__table15343138128>`.    |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
      | target          | Yes             | Object          | Specifies the restoration target.                                   |
      |                 |                 |                 |                                                                     |
      |                 |                 |                 | For details, see :ref:`Table 5 <rds_09_0009__table13185192412159>`. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

   .. _rds_09_0009__table15343138128:

   .. table:: **Table 4** source field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                               |
      +=================+=================+=================+===========================================================================================================================================+
      | instance_id     | Yes             | String          | Specifies the DB instance ID.                                                                                                             |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | type            | No              | String          | Specifies the restoration mode. Enumerated values include:                                                                                |
      |                 |                 |                 |                                                                                                                                           |
      |                 |                 |                 | -  **backup**: indicates using backup files for restoration. In this mode, **type** is not mandatory and **backup_id** is mandatory.      |
      |                 |                 |                 | -  **timestamp**: indicates the point-in-time restoration mode. In this mode, **type** is mandatory and **restore_time** is no mandatory. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_id       | No              | String          | Specifies the ID of the backup used to restore data. This parameter must be specified when the backup file is used for restoration.       |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | restore_time    | No              | Integer         | Specifies the time point of data restoration in the UNIX timestamp. The unit is millisecond and the time zone is UTC.                     |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0009__table13185192412159:

   .. table:: **Table 5** target field data structure description

      +-------------+-----------+--------+--------------------------------------------------------+
      | Name        | Mandatory | Type   | Description                                            |
      +=============+===========+========+========================================================+
      | instance_id | Yes       | String | Specifies the ID of the DB instance to be restored to. |
      +-------------+-----------+--------+--------------------------------------------------------+

-  Example

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/recovery

-  Request example

   Use backup files for restoration:

   .. code-block:: text

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

   Use PITR for restoration:

   .. code-block:: text

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

Response
--------

-  Normal response

   .. table:: **Table 6** Parameter description

      ====== ====== ======================
      Name   Type   Description
      ====== ====== ======================
      job_id String Indicates the task ID.
      ====== ====== ======================

-  Example normal response

   .. code-block:: text

      {
          "job_id": "ff80808157127d9301571bf8160c001d"
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
