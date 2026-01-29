:original_name: rds_07_0002.html

.. _rds_07_0002:

Querying Slow Query Log Statistics
==================================

Function
--------

This API is used to query slow query log statistics of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is available only to RDS for MySQL and RDS for PostgreSQL.

URI
---

-  URI format

   POST https://{*endpoint*}/v3.1/{project_id}/instances/{instance_id}/slow-logs/statistics

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | ID of the instance to be queried.                                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================+
   | start_time      | Yes             | String          | Start time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time        | Yes             | String          | End time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. You can only query slow logs generated within a month. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Index offset. The default value is **0**, indicating that the query starts from the first piece of data.                                                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of records (query results) displayed on each page. The number ranges from 1 to 100. The default value is **10**.                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Statement type. If this parameter is left empty, all statement types are queried.                                                                                         |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | Enumerated values:                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | -  INSERT                                                                                                                                                                 |
   |                 |                 |                 | -  UPDATE                                                                                                                                                                 |
   |                 |                 |                 | -  SELECT                                                                                                                                                                 |
   |                 |                 |                 | -  DELETE                                                                                                                                                                 |
   |                 |                 |                 | -  CREATE                                                                                                                                                                 |
   |                 |                 |                 | -  ALL                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | database        | No              | String          | Database name. It cannot contain special characters such as < > &.                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort            | No              | String          | Sorting field.                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | -  **executeTime**: indicates sorting slow query logs by average execution time in descending order.                                                                      |
   |                 |                 |                 | -  If this parameter is left empty or set to other values, the slow query logs are sorted by executions in descending order.                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | order           | No              | String          | Sorting sequence. The default value is **desc**.                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | Enumerated values:                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | -  desc                                                                                                                                                                   |
   |                 |                 |                 | -  asc                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Query slow query log statistics. Each page contains 10 records.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3.1/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/slow-logs/statistics
   {
       "start_time":"2023-01-05T08:00:00+0800",
       "end_time":"2023-01-11T20:00:00+0800",
       "limit":10,
       "order":"asc"
   }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                     |
      +=======================+=======================+=================================================================================================+
      | slow_log_list         | Array of objects      | Data set                                                                                        |
      |                       |                       |                                                                                                 |
      |                       |                       | For details, see :ref:`Table 5 <rds_07_0002__en-us_topic_0000001496833745_table1950773843311>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | total_count           | Integer               | Total number of records.                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+

   .. _rds_07_0002__en-us_topic_0000001496833745_table1950773843311:

   .. table:: **Table 5** slow_log_list field data structure description

      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Name          | Type   | Description                                                                                                                                 |
      +===============+========+=============================================================================================================================================+
      | count         | String | Number of executions.                                                                                                                       |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | time          | String | Average execution duration.                                                                                                                 |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | lock_time     | String | Average waiting time before locking. Only RDS for MySQL supports this parameter.                                                            |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | rows_sent     | Long   | Average number of rows contained in a result. Only RDS for MySQL supports this parameter.                                                   |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | rows_examined | Long   | Average number of scanned rows. Only RDS for MySQL supports this parameter.                                                                 |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | database      | String | Database which slow logs belong to. If any database name contains special characters such as < > ', the special characters will be escaped. |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | users         | String | User account.                                                                                                                               |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | query_sample  | String | Execution syntax.                                                                                                                           |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | client_ip     | String | IP address.                                                                                                                                 |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | type          | String | Statement type.                                                                                                                             |
      +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
        "slow_log_list" : [ {
          "count" : "9 (100.00%)",
          "time" : "3.00018 s",
          "lock_time" : "0.00000 s",
          "rows_sent" : 1,
          "rows_examined" : 0,
          "database" : "test_db",
          "users" : "root",
          "query_sample" : "SELECT sleep(N) LIMIT N, N;",
          "client_ip" : "100.*.*.247",
          "type" : "SELECT"
        } ],
        "total_count" : 1
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
