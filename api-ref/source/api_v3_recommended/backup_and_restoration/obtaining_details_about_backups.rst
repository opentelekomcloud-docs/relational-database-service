:original_name: rds_09_0005.html

.. _rds_09_0005:

Obtaining Details About Backups
===============================

Function
--------

This API is used to obtain details about backups.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is used to query full backups of MySQL, PostgreSQL, and Microsoft SQL Server databases and incremental backups of MySQL and PostgreSQL databases.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/backups?instance_id={instance_id}&backup_id={backup_id}&backup_type={backup_type}&offset={offset}&limit={limit}&begin_time={begin \_time}&end_time={end_time}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                                                                                                                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_id             | No                    | Specifies the backup ID.                                                                                                                                                                                                                            |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_type           | No                    | Specifies the backup type. Value:                                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | -  **auto**: automated full backup                                                                                                                                                                                                                  |
      |                       |                       | -  **manual**: manual full backup                                                                                                                                                                                                                   |
      |                       |                       | -  **fragment**: differential full backup                                                                                                                                                                                                           |
      |                       |                       | -  **incremental**: automated incremental backup                                                                                                                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Specifies the index position. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value must be a positive number. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Specifies the number of records to be queried. The default value is **100**. The value cannot be a negative number. The minimum value is **1** and the maximum value is **100**.                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | begin_time            | No                    | Specifies the start time for obtaining the backup list. The format of the start time is "yyyy-mm-ddThh:mm:ssZ".                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | .. note::                                                                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       |    When **begin_time** is not empty, **end_time** is mandatory.                                                                                                                                                                                     |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time              | No                    | Specifies the end time for obtaining the backup list. The format of the end time is "yyyy-mm-ddThh:mm:ssZ" and the end time must be later than the start time.                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | .. note::                                                                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       |    When **end_time** is not empty, **begin_time** is mandatory.                                                                                                                                                                                     |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/backups?instance_id=43e4feaab48f11e89039fa163ebaa7e4br01&backup_id=c0c9f155c7b7423a9d30f0175998b63bbr01&backup_type=auto&offset=0&limit=10&begin_time=2018-08-06T10:41:14+0800&end_time=2018-08-16T10:41:14+0800

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------+
      | Name                  | Type                  | Description                                                   |
      +=======================+=======================+===============================================================+
      | backups               | Array of objects      | Indicates the backup list.                                    |
      |                       |                       |                                                               |
      |                       |                       | For details, see :ref:`Table 3 <rds_09_0005__table52869820>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------+
      | total_count           | Integer               | Indicates the total number of records.                        |
      +-----------------------+-----------------------+---------------------------------------------------------------+

   .. _rds_09_0005__table52869820:

   .. table:: **Table 3** backups field data structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================+
      | id                    | String                | Indicates the backup ID.                                                                                                                               |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the backup name.                                                                                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | Indicates the backup type. Value:                                                                                                                      |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | -  **auto**: automated full backup                                                                                                                     |
      |                       |                       | -  **manual**: manual full backup                                                                                                                      |
      |                       |                       | -  **fragment**: differential full backup                                                                                                              |
      |                       |                       | -  **incremental**: automated incremental backup                                                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size                  | Long                  | Indicates the backup size in kB.                                                                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the backup status. Value:                                                                                                                    |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | -  BUILDING: Backup in progress                                                                                                                        |
      |                       |                       | -  COMPLETED: Backup completed                                                                                                                         |
      |                       |                       | -  FAILED: Backup failed                                                                                                                               |
      |                       |                       | -  DELETING: Backup being deleted                                                                                                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | begin_time            | String                | Indicates the backup start time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                  |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time              | String                | Indicates the backup end time.                                                                                                                         |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | -  In a full backup, it indicates the full backup end time.                                                                                            |
      |                       |                       | -  In a MySQL incremental backup, it indicates the time when the last transaction in the backup file is submitted.                                     |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | The format is yyyy-mm-ddThh:mm:ssZ. **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore             | Object                | Indicates the database version.                                                                                                                        |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | For details, see :ref:`Table 4 <rds_09_0005__table32267243>`.                                                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | databases             | Array of objects      | Indicates a list of self-built Microsoft SQL Server databases that support partial backups.                                                            |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | For details, see :ref:`Table 5 <rds_09_0005__table4541911203517>`.                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | String                | Indicates the ID of the DB instance for which the backup is created.                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0005__table32267243:

   .. table:: **Table 4** datastore field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                             |
      +=======================+=======================+=========================================================================================+
      | type                  | String                | Indicates the DB engine. Its value can be any of the following and is case-insensitive: |
      |                       |                       |                                                                                         |
      |                       |                       | -  MySQL                                                                                |
      |                       |                       | -  PostgreSQL                                                                           |
      |                       |                       | -  SQLServer                                                                            |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | version               | String                | Indicates the database version.                                                         |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

   .. _rds_09_0005__table4541911203517:

   .. table:: **Table 5** databases field data structure description

      ==== ====== ==============================================
      Name Type   Description
      ==== ====== ==============================================
      name String Indicates the name of the self-built database.
      ==== ====== ==============================================

-  Example normal response

   Obtaining a backup list of a MySQL DB instance:

   .. code-block:: text

      {
          "backups": [{
              "id": "43e4feaab48f11e89039fa163ebaa7e4br01",
              "name": "xxxx.xxx",
              "type": "auto",
              "size": 2803,
              "status": "COMPLETED",
              "begin_time": "2018-08-06T12:41:14+0800",
              "end_time": "2018-08-06T12:43:14+0800",
              "datastore": {
                  "type": "MySQL",
                  "version": "8.0"
              },
              "instance_id": "a48e43ff268f4c0e879652d65e63d0fbin01"
          }],
          "total_count": 1
      }

   Obtaining a backup list of a PostgreSQL DB instance:

   .. code-block:: text

      {
          "backups": [{
              "id": "43e4feaab48f11e89039fa163ebaa7e4br03",
              "name": "xxxx.xxx",
              "type": "incremental",
              "size": 2803,
              "status": "COMPLETED",
              "begin_time": "2018 - 08 - 06 T12: 41: 14 + 0800",
              "end_time": "2018 - 08 - 06 T12: 43: 14 + 0800",
              "datastore": {
                  "type": "PostgreSQL",
                  "version": "13"
              },
              "instance_id": "a48e43ff268f4c0e879652d65e63d0fbin03 "
          }],
          "total_count": 1
      }

   Obtaining a backup list of a Microsoft SQL Server DB instance:

   .. code-block:: text

      {
          "backups": [{
              "id ": "43e4feaab48f11e89039fa163ebaa7e4br04",
              "name": "xxxx.xxx",
              "type": "manual",
              "size": 2803,
              "status": "COMPLETED",
              "begin_time": "2018-08-06T12:41:14+0800",
              "end_time": "2018-08-06T12:43:14+0800",
              "datastore": {
                  "type": "SQLServer",
                  "version": "2017_SE"
              },
              "databases": [{
                  "name": "user01"
              }, {
                  "name": "user02"
              }],
              "instance_id": "a48e43ff268f4c0e879652d65e63d0fbin04"
          }],
          "total_count": 1
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
