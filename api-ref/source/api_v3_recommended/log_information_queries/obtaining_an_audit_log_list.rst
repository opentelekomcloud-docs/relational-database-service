:original_name: rds_log_0003.html

.. _rds_log_0003:

Obtaining an Audit Log List
===========================

Function
--------

This API is used to obtain an audit log list.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is available only to RDS for MySQL.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/auditlog?start_time={start_time}&end_time={end_time}&offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                                                           |
      +=======================+=======================+=======================================================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                       |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the ID of the queried DB instance.                                                                                                                                                                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time            | Yes                   | Specifies the start time for obtaining the backup list. The format of the start time is "yyyy-mm-ddThh:mm:ssZ".                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time              | Yes                   | Specifies the end time for obtaining the backup list. The format of the end time is "yyyy-mm-ddThh:mm:ssZ" and the end time must be later than the start time. The time span cannot be longer than 30 days.           |
      |                       |                       |                                                                                                                                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | Yes                   | Specifies the index position.                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                       |
      |                       |                       | If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value must be a positive number. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | Yes                   | Specifies the number of records to be queried. The value range is from 1 to 50.                                                                                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/auditlog?start_time=2019-11-06T09:00:00+0800&end_time=2019-11-07T10:40:15+0800&offset=0&limit=10

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------+
      | Name                  | Type                  | Description                                                    |
      +=======================+=======================+================================================================+
      | auditlogs             | Array of objects      | Indicates detailed information.                                |
      |                       |                       |                                                                |
      |                       |                       | For details, see :ref:`Table 3 <rds_log_0003__table66531170>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------+
      | total_record          | Integer               | Indicates the total number of records.                         |
      +-----------------------+-----------------------+----------------------------------------------------------------+

   .. _rds_log_0003__table66531170:

   .. table:: **Table 3** auditlogs field data structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | id                    | String                | Indicates the audit log ID.                                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the audit log file name.                                                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | size                  | Long                  | Indicates the size in KB of the audit log.                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | begin_time            | String                | Indicates the start time of the audit log. The format is "yyyy-mm-ddThh:mm:ssZ".                                   |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | end_time              | String                | Indicates the end time of the audit log. The format is "yyyy-mm-ddThh:mm:ssZ".                                     |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "auditlogs": [{
              "id": "fa163ea0e2bet11e9d832166a2cf894c5br01",
              "name": "317156_20190916032844_eb8fe5d181ec44a2850302691541f760in01_Audit_166a2cf8-d832-11e9-94c5-fa163ea0e2be",
              "size": 20481.835938,
              "begin_time": "2019-11-06T09:03:34+0800",
              "end_time": "2019-11-06T10:39:15+0800"
          }, {
              "id": "fa163ea0e2bet11e9d832136a668094c5br01",
              "name": "317162_20190916032838_eb8fe5d181ec44a2850302691541f760in01_Audit_136a6680-d832-11e9-94c5-fa163ea0e2be",
              "size": 20481.835938,
              "begin_time": "2019-11-07T09:04:35+0800",
              "end_time":"2019-11-07T10:38:16+0800"
          }],
          "total_record": 2
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
