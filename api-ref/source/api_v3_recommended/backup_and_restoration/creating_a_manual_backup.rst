:original_name: rds_09_0004.html

.. _rds_09_0004:

Creating a Manual Backup
========================

Function
--------

This API is used to create a manual backup.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  Read replicas do not support manual backup creation.
-  The backup name must be unique.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/backups

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/backups

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

      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type             | Description                                                                                                                                                                              |
      +=================+=================+==================+==========================================================================================================================================================================================+
      | instance_id     | Yes             | String           | Specifies the DB instance ID.                                                                                                                                                            |
      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | Yes             | String           | Specifies the backup name. It must be 4 to 64 characters in length and start with a letter. It is case-sensitive and can contain only letters, digits, hyphens (-), and underscores (_). |
      |                 |                 |                  |                                                                                                                                                                                          |
      |                 |                 |                  | The backup name must be unique.                                                                                                                                                          |
      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String           | Specifies the backup description. It contains a maximum of 256 characters and cannot contain the following special characters: >!<"&'=                                                   |
      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | databases       | No              | Array of objects | Specifies a list of self-built Microsoft SQL Server databases that are partially backed up. (Only Microsoft SQL Server support partial backups.)                                         |
      |                 |                 |                  |                                                                                                                                                                                          |
      |                 |                 |                  | For details, see :ref:`Table 3 <rds_09_0004__table917312715167>`.                                                                                                                        |
      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0004__table917312715167:

   .. table:: **Table 3** databases field data structure description

      ==== ========= ====== ============================================
      Name Mandatory Type   Description
      ==== ========= ====== ============================================
      name Yes       String Specifies the names of self-built databases.
      ==== ========= ====== ============================================

-  Request example

   .. code-block:: text

      {
          "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin01",
          "name": "backup",
      "description": "manual backup"
      }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                       |
      +=======================+=======================+===================================================================+
      | backup                | Object                | Indicates the backup information.                                 |
      |                       |                       |                                                                   |
      |                       |                       | For details, see :ref:`Table 5 <rds_09_0004__table153397472217>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------+

   .. _rds_09_0004__table153397472217:

   .. table:: **Table 5** backup field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================================+
      | id                    | String                | Indicates the backup ID.                                                                                                                                            |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | String                | Indicates the DB instance ID.                                                                                                                                       |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the backup name.                                                                                                                                          |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Indicates the backup description.                                                                                                                                   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | databases             | Array of objects      | Indicates a list of self-built Microsoft SQL Server databases that are partially backed up. (Only Microsoft SQL Server support partial backups.)                    |
      |                       |                       |                                                                                                                                                                     |
      |                       |                       | For details, see :ref:`Table 3 <rds_09_0004__table917312715167>`.                                                                                                   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | begin_time            | String                | Indicates the backup start time in the "yyyy-mm-ddThh:mm:ssZ" format, where "T" indicates the start time of the time field, and "Z" indicates the time zone offset. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the backup status. Value:                                                                                                                                 |
      |                       |                       |                                                                                                                                                                     |
      |                       |                       | -  BUILDING: Backup in progress                                                                                                                                     |
      |                       |                       | -  COMPLETED: Backup completed                                                                                                                                      |
      |                       |                       | -  FAILED: Backup failed                                                                                                                                            |
      |                       |                       | -  DELETING: Backup being deleted                                                                                                                                   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | Indicates the backup type. Value:                                                                                                                                   |
      |                       |                       |                                                                                                                                                                     |
      |                       |                       | -  auto: automated full backup                                                                                                                                      |
      |                       |                       | -  manual: manual full backup                                                                                                                                       |
      |                       |                       | -  fragment: differential full backup                                                                                                                               |
      |                       |                       | -  incremental: automated incremental backup                                                                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "backup": {
              "id": "2f4ddb93-b901-4b08-93d8-1d2e472f30fe",
              "name": "backupDemo",
              "description": "This is a description",
              "begin_time": "2016-09-12T01:17:05",
              "status": "BUILDING",
              "type": "manual",
              "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin01"
          }
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
