:original_name: en-us_topic_0057306831.html

.. _en-us_topic_0057306831:

Querying an API Version List (Compatible with OpenStack)
========================================================

Function
--------

This API is used to query the currently supported RDS API version list.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   PATH: /

   Method: GET

-  Parameter description

   None

Request
-------

None

Response
--------

-  Normal response

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                  |
      +=======================+=======================+==============================================================================================+
      | versions              | Array of objects      | Indicates the list of detailed API version information.                                      |
      |                       |                       |                                                                                              |
      |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0057306831__t597bb32ec3694c8e917e7b92cbcc8b18>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+

   .. _en-us_topic_0057306831__t597bb32ec3694c8e917e7b92cbcc8b18:

   .. table:: **Table 2** versions field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                           |
      +=======================+=======================+=======================================================================================================+
      | id                    | String                | Indicates the API version.                                                                            |
      |                       |                       |                                                                                                       |
      |                       |                       | -  **v1**: indicates the API v1 version.                                                              |
      |                       |                       | -  **v1.0**: indicates the OpenStack trove API v1.0.                                                  |
      |                       |                       | -  **v3**: indicates the API v3 version.                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | links                 | Array of objects      | Indicates the API link information. The value is empty when the version is **v1** or **v3**.          |
      |                       |                       |                                                                                                       |
      |                       |                       | For details, see :ref:`Table 3 <en-us_topic_0057306831__t645d6d81bf2f42a18f1a65676a7219d7>`.          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the version status.                                                                         |
      |                       |                       |                                                                                                       |
      |                       |                       | The value **CURRENT** indicates that the version has been released.                                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the version update time.                                                                    |
      |                       |                       |                                                                                                       |
      |                       |                       | The format is yyyy-mm-dd Thh:mm:ssZ.                                                                  |
      |                       |                       |                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the UTC. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0057306831__t645d6d81bf2f42a18f1a65676a7219d7:

   .. table:: **Table 3** links field data structure description (dedicated for OpenStack v1.0)

      +------+--------+------------------------------------------------------------------+
      | Name | Type   | Description                                                      |
      +======+========+==================================================================+
      | href | String | Indicates the API URL and the value is **""**.                   |
      +------+--------+------------------------------------------------------------------+
      | rel  | String | Its value is **self**, indicating that **href** is a local link. |
      +------+--------+------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
       "versions": [
              {
                 "id": "v1",
                 "links": [],
                 "status": "CURRENT",
                 "updated": "2017-02-07T17:34:02Z"
              },
              {
                  "id": "v1.0",
                  "links": [
                       {
                           "href": "",
                           "rel": "self"
                       }
                  ],
                  "status": "CURRENT",
                  "updated": "2017-03-23T17:34:02Z"
              } ,
           {
                 "id": "v3",
                 "links": [],
                 "status": "CURRENT",
                 "updated": "2019-01-15T12:00:00Z"
              }
          ]
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
