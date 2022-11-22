:original_name: en-us_topic_0037147511.html

.. _en-us_topic_0037147511:

Querying Database Slow Logs
===========================

Function
--------

This API is used to query database slow logs.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/slowlog

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | instanceId            | Yes                   | Specifies the primary node ID of the DB instance.                                                                            |
      |                       |                       |                                                                                                                              |
      |                       |                       | .. note::                                                                                                                    |
      |                       |                       |                                                                                                                              |
      |                       |                       |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

-  Restrictions

   Only MySQL DB instances are supported.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================+
      | sftype                | No                    | Specifies the statement type. Its value can be empty, **INSERT**, **UPDATE**, **SELECT**, **DELETE**, or **CREATE**. If the value is empty, all statement types exist. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | top                   | No                    | Specifies how many records are returned.                                                                                                                               |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | -  If this parameter is specified, the value range is from 1 to 50.                                                                                                    |
      |                       |                       | -  If this parameter is not specified, the first 10 records are returned.                                                                                              |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      /rds/v1/68e3010955d748099f62a0df726fe09b/instances/02e47383-9222-4d29-bf5b-54b3013b0f71/slowlog?sftype=&top=10

Normal Response
---------------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-------------+-----------------------------------------------------------------------------------------------+----------------------------------------+
      | Name        | Type                                                                                          | Description                            |
      +=============+===============================================================================================+========================================+
      | slowLogList | List data structure. For details, see :ref:`Table 4 <en-us_topic_0037147511__table66531170>`. | Indicates detailed information.        |
      +-------------+-----------------------------------------------------------------------------------------------+----------------------------------------+
      | totalRecord | Int                                                                                           | Indicates the total number of records. |
      +-------------+-----------------------------------------------------------------------------------------------+----------------------------------------+

   .. _en-us_topic_0037147511__table66531170:

   .. table:: **Table 4** slowLogList field data structure description

      +--------------+--------+-------------------------------------------------------------+
      | Name         | Type   | Description                                                 |
      +==============+========+=============================================================+
      | count        | String | Indicates the number of executions.                         |
      +--------------+--------+-------------------------------------------------------------+
      | time         | String | Indicates the average execution duration.                   |
      +--------------+--------+-------------------------------------------------------------+
      | lockTime     | String | Indicates the average waiting time before locking.          |
      +--------------+--------+-------------------------------------------------------------+
      | rowsSent     | String | Indicates the average number of rows contained in a result. |
      +--------------+--------+-------------------------------------------------------------+
      | rowsExamined | String | Indicates the average number of scanned rows.               |
      +--------------+--------+-------------------------------------------------------------+
      | database     | String | Indicates the database which the slow log belongs to.       |
      +--------------+--------+-------------------------------------------------------------+
      | users        | String | Indicates the account.                                      |
      +--------------+--------+-------------------------------------------------------------+
      | querySample  | String | Indicates the execution syntax.                             |
      +--------------+--------+-------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {    "slowLogList": [
              {
                  "count": " 409  (99.76%)",
                  "time": "1.29",
                  "lockTime": " 0 ",
                  "rowsSent": " 0 ",
                  "rowsExamined": " 0 ",
                  "database": " ",
                  "users": " \trdsBackup@localhost  : 100.00% (409) of query, 99.76% (409) of all users",
                  "querySample": "flush logs;"
              },
              {
                  "count": " 1  (0.24%)",
                  "time": "5.0",
                  "lockTime": " 0 ",
                  "rowsSent": " 1 ",
                  "rowsExamined": " 0 ",
                  "database": " ",
                  "users": " \trdsAdmin@localhost  : 100.00% (1) of query, 0.24% (1) of all users",
                  "querySample": "select sleep(5);"
              }
          ],
          "totalRecord": 2
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
