:original_name: rds_06_0004.html

.. _rds_06_0004:

Querying Database Error Logs
============================

Function
--------

This API is used to query the latest 2000 database error logs.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/errorlog?start_date={start_date}&end_date={end_date}

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/errorlog?offset=1&limit=10&start_date=2018-08-06T10:41:14+0800&end_date=2018-08-07T10:41:14+0800&level=ALL

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                             |
      |                       |                       |                                                                                                                                               |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the ID of the queried DB instance.                                                                                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | start_date            | Yes                   | Specifies the start time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                |
      |                       |                       |                                                                                                                                               |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                            |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | end_date              | Yes                   | Specifies the end time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                  |
      |                       |                       |                                                                                                                                               |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                            |
      |                       |                       |                                                                                                                                               |
      |                       |                       | You can only query error logs generated within a month.                                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Specifies the page offset, such as 1, 2, 3, or 4. The parameter value is **1** by default if it is not specified.                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Specifies the number of records on a page. Its value range is from 1 to 100. The parameter value is **10** by default if it is not specified. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | level                 | No                    | Specifies the log level. The default value is **ALL**. Valid value:                                                                           |
      |                       |                       |                                                                                                                                               |
      |                       |                       | -  ALL                                                                                                                                        |
      |                       |                       | -  INFO                                                                                                                                       |
      |                       |                       | -  LOG                                                                                                                                        |
      |                       |                       | -  WARNING                                                                                                                                    |
      |                       |                       | -  ERROR                                                                                                                                      |
      |                       |                       | -  FATAL                                                                                                                                      |
      |                       |                       | -  PANIC                                                                                                                                      |
      |                       |                       | -  NOTE                                                                                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------+
      | Name                  | Type                  | Description                                                   |
      +=======================+=======================+===============================================================+
      | error_log_list        | Array of objects      | Indicates detailed information.                               |
      |                       |                       |                                                               |
      |                       |                       | For details, see :ref:`Table 3 <rds_06_0004__table66531170>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------+
      | total_record          | Integer               | Indicates the total number of records.                        |
      +-----------------------+-----------------------+---------------------------------------------------------------+

   .. _rds_06_0004__table66531170:

   .. table:: **Table 3** error_log_list field data structure description

      ======= ====== =====================================
      Name    Type   Description
      ======= ====== =====================================
      time    String Indicates the time in the UTC format.
      level   String Indicates the log level.
      content String Indicates the log content.
      ======= ====== =====================================

-  Example normal response

   .. code-block:: text

      {
          "error_log_list": [{
              "time": "2018-12-04T14:24:42",
              "level": "ERROR",
              "content": "Slave I/O for channel '': error connecting to master 'rdsRepl@172.16.30.111:3306' - retry-time: 60  retries: 1, Error_code: 203"
          }, {
              "time": "2018-12-04T14:24:42",
              "level": "ERROR",
              "content": "Slave I/O for channel '': error connecting to master 'rdsRepl@172.11.11.111:8081' - retry-time: 60  retries: 1, Error_code: 203"
          }],
          "total_record": 2
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
