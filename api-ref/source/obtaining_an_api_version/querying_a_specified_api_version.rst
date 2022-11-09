:original_name: en-us_topic_0032347779.html

.. _en-us_topic_0032347779:

Querying a Specified API Version
================================

Function
--------

This API is used to query the specified API version.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/rds/{*versionId*}

-  Example

   https://rds.eu-de.otc.t-systems.com/rds/v1

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                               |
      +=======================+=======================+===========================================================================================================================================================+
      | versionId             | Yes                   | Specifies the API version. It is case-sensitive.                                                                                                          |
      |                       |                       |                                                                                                                                                           |
      |                       |                       | For details, see **id** in :ref:`Table 2 <en-us_topic_0032347778__table37479565104653>` in section :ref:`Querying API Versions <en-us_topic_0032347778>`. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                    |
      +=======================+=======================+================================================================================+
      | versions              | Object                | Indicates the list of detailed API version information.                        |
      |                       |                       |                                                                                |
      |                       |                       | For details, see :ref:`Table 3 <en-us_topic_0032347779__table57914909154838>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------+
      | version               | Object                | Indicates the list of detailed API version information.                        |
      |                       |                       |                                                                                |
      |                       |                       | For details, see :ref:`Table 3 <en-us_topic_0032347779__table57914909154838>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------+

   .. _en-us_topic_0032347779__table57914909154838:

   .. table:: **Table 3** versions field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                           |
      +=======================+=======================+=======================================================================================================+
      | id                    | String                | Indicates the API version.                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | links                 | Array                 | Indicates the API version link information. Its value is empty.                                       |
      |                       |                       |                                                                                                       |
      |                       |                       | For details, see :ref:`Table 4 <en-us_topic_0032347779__table630875915440>`.                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the version status.                                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the version update time.                                                                    |
      |                       |                       |                                                                                                       |
      |                       |                       | The format is yyyy-mm-dd Thh:mm:ssZ.                                                                  |
      |                       |                       |                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the UTC. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0032347779__table630875915440:

   .. table:: **Table 4** links field data structure description

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
        "version": {
          "id": "v1",
          "links": [],
          "status": "CURRENT",
          "updated": "2017-02-07T17:34:02Z"
        },
        "versions": {
          "id": "v1",
          "links": [],
          "status": "CURRENT",
          "updated": "2017-02-07T17:34:02Z"
        }
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
