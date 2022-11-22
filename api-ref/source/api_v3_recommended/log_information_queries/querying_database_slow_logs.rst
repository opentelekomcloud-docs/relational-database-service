:original_name: rds_06_0005.html

.. _rds_06_0005:

Querying Database Slow Logs
===========================

Function
--------

This API is used to query the latest 2000 database slow query logs.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

Only the MySQL DB instances are supported.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/slowlog?start_date={start_date}&end_date={end_date}

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/slowlog?offset=1&limit=10&start_date=2018-08-06T10:41:14+0800&end_date=2018-08-07T10:41:14+0800&type=INSERT

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                               |
      +=======================+=======================+===========================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                         |
      |                       |                       |                                                                                                                                                                           |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                          |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the ID of the queried DB instance.                                                                                                                              |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_date            | Yes                   | Specifies the start date in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                            |
      |                       |                       |                                                                                                                                                                           |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_date              | Yes                   | Specifies the end time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                              |
      |                       |                       |                                                                                                                                                                           |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. You can only query slow logs generated within a month. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Specifies the page offset, such as 1, 2, 3, or 4. The parameter value is **1** by default if it is not specified.                                                         |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Specifies the number of records on a page. Its value range is from 1 to 100. The parameter value is **10** by default if it is not specified.                             |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | No                    | Specifies the statement type. If it is left blank, all statement types are queried. Valid value:                                                                          |
      |                       |                       |                                                                                                                                                                           |
      |                       |                       | -  INSERT                                                                                                                                                                 |
      |                       |                       | -  UPDATE                                                                                                                                                                 |
      |                       |                       | -  SELECT                                                                                                                                                                 |
      |                       |                       | -  DELETE                                                                                                                                                                 |
      |                       |                       | -  CREATE                                                                                                                                                                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
      | slow_log_list         | Array of objects      | Indicates detailed information.                               |
      |                       |                       |                                                               |
      |                       |                       | For details, see :ref:`Table 3 <rds_06_0005__table66531170>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------+
      | total_record          | Integer               | Indicates the total number of records.                        |
      +-----------------------+-----------------------+---------------------------------------------------------------+

   .. _rds_06_0005__table66531170:

   .. table:: **Table 3** slow_log_list field data structure description

      +---------------+--------+-------------------------------------------------------+
      | Name          | Type   | Description                                           |
      +===============+========+=======================================================+
      | count         | String | Indicates the number of executions.                   |
      +---------------+--------+-------------------------------------------------------+
      | time          | String | Indicates the execution time.                         |
      +---------------+--------+-------------------------------------------------------+
      | lock_time     | String | Indicates the lock wait time.                         |
      +---------------+--------+-------------------------------------------------------+
      | rows_sent     | String | Indicates the number of sent rows.                    |
      +---------------+--------+-------------------------------------------------------+
      | rows_examined | String | Indicates the number of scanned rows.                 |
      +---------------+--------+-------------------------------------------------------+
      | database      | String | Indicates the database which the slow log belongs to. |
      +---------------+--------+-------------------------------------------------------+
      | users         | String | Indicates the account.                                |
      +---------------+--------+-------------------------------------------------------+
      | query_sample  | String | Indicates the execution syntax.                       |
      +---------------+--------+-------------------------------------------------------+
      | type          | String | Indicates the statement type.                         |
      +---------------+--------+-------------------------------------------------------+
      | start_time    | String | Indicates the time in the UTC format.                 |
      +---------------+--------+-------------------------------------------------------+
      | client_ip     | String | Indicates the IP address.                             |
      +---------------+--------+-------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "total_record": 1,
          "slow_log_list": [
              {
                  "count": "1",
                  "time": "1.04899 s",
                  "lock_time": "0.00003 s",
                  "rows_sent": "0",
                  "rows_examined": "0",
                  "database": "mysql",
                  "users": "root",
                  "query_sample": "INSERT INTO time_zone_name (Name, Time_zone_id) VALUES (N, @time_zone_id);",
                  "type": "INSERT",
                  "start_time": "2018-08-06T10:41:14",
                  "client_ip": "192.*.*.1"
              }
          ]
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
