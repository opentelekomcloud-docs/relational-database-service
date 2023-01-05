:original_name: rds_06_0100.html

.. _rds_06_0100:

Obtaining Slow Query Log Statistics
===================================

Function
--------

This API is used to query and collect statistics on slow query logs based on service requirements.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is supported for MySQL only.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/slowlog/statistics?cur_page={cur_page}&per_page={per_page}&type={type}&start_date={start_date}&end_date={end_date}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                  |
      |                       |                       |                                                                                                                    |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the ID of the DB instance to be queried.                                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | cur_page              | Yes                   | Specifies the page offset (the current page number, such as 1, 2, 3, or 4.)                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | per_page              | Yes                   | Specifies the number of records on each page. The value ranges from 0 to 100.                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | start_date            | Yes                   | Specifies the start date in the "yyyy-mm-ddThh:mm:ssZ" format.                                                     |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | end_date              | Yes                   | Specifies the end time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                       |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | type                  | Yes                   | Specifies the statement type. If it is left blank, all statement types are queried. Valid value:                   |
      |                       |                       |                                                                                                                    |
      |                       |                       | -  INSERT                                                                                                          |
      |                       |                       | -  UPDATE                                                                                                          |
      |                       |                       | -  SELECT                                                                                                          |
      |                       |                       | -  DELETE                                                                                                          |
      |                       |                       | -  CREATE                                                                                                          |
      |                       |                       | -  ALL                                                                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/slowlog/statistics?cur_page=1&per_page=2&type=INSERT&start_date=2020-02-06T10:41:14+0800&end_date=2020-02-07T10:41:14+0800

Response
--------

-  Normal response

   .. table:: **Table 2** Description

      +-------------+---------+------------------------------------------------------------------------------+
      | Name        | Type    | Description                                                                  |
      +=============+=========+==============================================================================+
      | pageNumber  | Integer | Indicates the current page number.                                           |
      +-------------+---------+------------------------------------------------------------------------------+
      | pageRecord  | Integer | Indicates the number of records on each page.                                |
      +-------------+---------+------------------------------------------------------------------------------+
      | slowLogList | List    | See :ref:`Table 3 <rds_06_0100__en-us_topic_0231893217_table1950773843311>`. |
      +-------------+---------+------------------------------------------------------------------------------+
      | totalRecord | Integer | Indicates the total number of records.                                       |
      +-------------+---------+------------------------------------------------------------------------------+

   .. _rds_06_0100__en-us_topic_0231893217_table1950773843311:

   .. table:: **Table 3** slow_log_list field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                             |
      +=======================+=======================+=========================================================================+
      | count                 | String                | Indicates the number of executions.                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | time                  | String                | Indicates the execution time.                                           |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | lockTime              | String                | Indicates the lock wait time.                                           |
      |                       |                       |                                                                         |
      |                       |                       | This parameter is not present in the response for PostgreSQL DB engine. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | rowsSent              | Long                  | Indicates the number of sent rows.                                      |
      |                       |                       |                                                                         |
      |                       |                       | This parameter is not present in the response for PostgreSQL DB engine. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | rowsExamined          | Long                  | Indicates the number of scanned rows.                                   |
      |                       |                       |                                                                         |
      |                       |                       | This parameter is not present in the response for PostgreSQL DB engine. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | database              | String                | Indicates the database which the slow log belongs to.                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | users                 | String                | Indicates the account.                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | querySample           | String                | Indicates the execution syntax.                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | type                  | String                | Indicates the statement type.                                           |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | clientIP              | String                | Indicates the IP address.                                               |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "pageNumber": 1,
          "pageRecord": 10,
          "slowLogList": [],
          "totalRecord": 0,
              "startTime": null,
              "endTime":null
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
