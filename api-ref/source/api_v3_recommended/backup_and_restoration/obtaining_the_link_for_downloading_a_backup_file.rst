:original_name: rds_09_0006.html

.. _rds_09_0006:

Obtaining the Link for Downloading a Backup File
================================================

Function
--------

This API is used to obtain the link for downloading a backup file.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is used to query full backups of MySQL, PostgreSQL, and Microsoft SQL Server databases and incremental backups of MySQL and PostgreSQL databases.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/backup-files?backup_id={backup_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | backup_id             | Yes                   | Specifies the backup ID.                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/97b026aa9cc4417888c14c84a1ad9860/backup-files?backup_id=c0c9f155c7b7423a9d30f0175998b63bbr01

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------+
      | Name                  | Type                  | Description                                                   |
      +=======================+=======================+===============================================================+
      | files                 | Array of objects      | Indicates the list of backup files.                           |
      |                       |                       |                                                               |
      |                       |                       | For details, see :ref:`Table 3 <rds_09_0006__table52869820>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------+
      | bucket                | String                | Indicates the name of the bucket where the file is located.   |
      +-----------------------+-----------------------+---------------------------------------------------------------+

   .. _rds_09_0006__table52869820:

   .. table:: **Table 3** files field data structure description

      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name              | Type   | Description                                                                                                                                                                                  |
      +===================+========+==============================================================================================================================================================================================+
      | name              | String | Indicates the file name.                                                                                                                                                                     |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size              | Long   | Indicates the file size in KB.                                                                                                                                                               |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | download_link     | String | Indicates the link for downloading the backup file.                                                                                                                                          |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | link_expired_time | String | Indicates the link expiration time. The format is "yyyy-mm-ddThh:mm:ssZ". **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | database_name     | String | Indicates the name of the database. If the backup file is not a database backup file, null is returned.                                                                                      |
      +-------------------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
         "files": [
          {
              "name": "43e4feaab48f11e89039fa163ebaa7e4br01.xxx",
              "size": 2803,
              "download_link":"https://obs.domainname.com/rdsbucket.username.1/xxxxxx",
              "link_expired_time":"2018-08-016T10:15:14+0800"
           }
           ],
          "bucket": "rdsbucket.bucketname"
      }

-  Abnormal response

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
