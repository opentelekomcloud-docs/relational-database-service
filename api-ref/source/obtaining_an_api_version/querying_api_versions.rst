:original_name: en-us_topic_0032347778.html

.. _en-us_topic_0032347778:

Querying API Versions
=====================

Function
--------

This API is used to query the currently supported RDS API versions.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/rds/

-  Example

   https://rds.eu-de.otc.t-systems.com/rds/

-  Parameter description

   None

Request
-------

None

Response
--------

-  Normal response

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                    |
      +=======================+=======================+================================================================================+
      | versions              | Array of objects      | Indicates the list of detailed API version information.                        |
      |                       |                       |                                                                                |
      |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0032347778__table37479565104653>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------+

   .. _en-us_topic_0032347778__table37479565104653:

   .. table:: **Table 2** versions field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                        |
      +=======================+=======================+====================================================================================================================================+
      | id                    | String                | Indicates the API version.                                                                                                         |
      |                       |                       |                                                                                                                                    |
      |                       |                       | -  **v1**: indicates the API v1 version.                                                                                           |
      |                       |                       | -  **v1.0**: indicates the OpenStack trove API v1.0.                                                                               |
      |                       |                       | -  **v3**: indicates the API v3 version.                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Array of objects      | Indicates the API link information. The value is empty when the version is **v1** or **v3**.                                       |
      |                       |                       |                                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 3 <en-us_topic_0032347778__table630875915440>`.                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the version status.                                                                                                      |
      |                       |                       |                                                                                                                                    |
      |                       |                       | **CURRENT**: indicates that the version is recommended.                                                                            |
      |                       |                       |                                                                                                                                    |
      |                       |                       | **DEPRECATED**: indicates a deprecated version which may be deleted later.                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the version update time.                                                                                                 |
      |                       |                       |                                                                                                                                    |
      |                       |                       | The format is yyyy-mm-dd Thh:mm:ssZ.                                                                                               |
      |                       |                       |                                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the Coordinated Universal Time (UTC). |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0032347778__table630875915440:

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
          "versions": [{
              "id": "v1",
              "links": [],
              "status": "CURRENT",
              "updated": "2017-02-07T17:34:02Z"
          }, {
              "id": "v1.0",
              "links": [{
                  "href": "",
                  "rel": "self"
              }],
              "status": "CURRENT",
              "updated": "2017-03-23T17:34:02Z"
          }, {
              "id": "v3",
              "links": [],
              "status": "CURRENT",
              "updated": "2019-01-15T12:00:00Z"
          }]
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
