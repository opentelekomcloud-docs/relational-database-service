:original_name: en-us_topic_0037147510.html

.. _en-us_topic_0037147510:

Querying Database Error Logs
============================

Function
--------

This API is used to query database error logs.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/errorlog

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

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                                                                              |
      +=======================+=======================+==========================================================================================================================================================================================================================================+
      | startDate             | Yes                   | Specifies the start time following a specified time translation rule. For example, time "2016-08-29+06:35" is translated into "2016-08-29+06%3A35", where "%3A" is translated from ":" and other digits and characters remain unchanged. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | endDate               | Yes                   | Specifies the end time following a specified time translation rule. For example, time "2016-08-29+06:35" is translated into "2016-08-29+06%3A35", where "%3A" is translated from ":" and other digits and characters remain unchanged.   |
      |                       |                       |                                                                                                                                                                                                                                          |
      |                       |                       | You can only query error logs generated within a month.                                                                                                                                                                                  |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | curPage               | No                    | Specifies the current page number, such as 1, 2, 3, or 4. The parameter value is **1** by default if it is not specified.                                                                                                                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | perPage               | No                    | Specifies the number of records on a page. Its value range is from 1 to 100. The parameter value is **10** by default if it is not specified.                                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      /rds/v1/68e3010955d748099f62a0df726fe09b/instances/02cf1fd7-24ae-4fec-a621-329ec732e4f6/errorlog?startDate=2016-08-29+06%3A35&endDate=2016-09-05+06%3A35&curPage=1&perPage=10

Normal Response
---------------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +--------------+-----------------------------------------------------------------------------------------------+----------------------------------------+
      | Name         | Type                                                                                          | Description                            |
      +==============+===============================================================================================+========================================+
      | errorLogList | List data structure. For details, see :ref:`Table 4 <en-us_topic_0037147510__table66531170>`. | Indicates detailed information.        |
      +--------------+-----------------------------------------------------------------------------------------------+----------------------------------------+
      | totalRecord  | Int                                                                                           | Indicates the total number of records. |
      +--------------+-----------------------------------------------------------------------------------------------+----------------------------------------+

   .. _en-us_topic_0037147510__table66531170:

   .. table:: **Table 4** errorLogList field data structure description

      ======== ====== ============================
      Name     Type   Description
      ======== ====== ============================
      datetime String Indicates the date and time.
      content  String Indicates the log content.
      ======== ====== ============================

-  Response example

   .. code-block:: text

      {
          "errorLogList": [
              {
                  "datetime": "2016-08-30 09:55:39",
                  "content": "[Warning] 'proxies_priv' entry '@ root@rds-bf83' ignored in --skip-name-resolve mode."
              }
          ],
          "totalRecord":1
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
