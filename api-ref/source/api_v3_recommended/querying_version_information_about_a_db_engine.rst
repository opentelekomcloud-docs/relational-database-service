:original_name: rds_06_0001.html

.. _rds_06_0001:

Querying Version Information About a DB Engine
==============================================

Function
--------

This API is used to query the database version information of a specified DB engine.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{*project_id*}/datastores/{*database_name*}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | database_name         | Yes                   | Specifies the DB engine. Its value can be any of the following and is case-insensitive:          |
      |                       |                       |                                                                                                  |
      |                       |                       | -  MySQL                                                                                         |
      |                       |                       | -  PostgreSQL                                                                                    |
      |                       |                       | -  SQLServer                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/619d3e78f61b4be68bc5aa0b59edcf7b/datastores/mysql

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------+
      | Name                  | Type                  | Description                                                   |
      +=======================+=======================+===============================================================+
      | dataStores            | Array of objects      | Indicates the list of database versions.                      |
      |                       |                       |                                                               |
      |                       |                       | For details, see :ref:`Table 3 <rds_06_0001__table66531170>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------+

   .. _rds_06_0001__table66531170:

   .. table:: **Table 3** dataStores field data structure description

      +------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name | Type   | Description                                                                                                                                                             |
      +======+========+=========================================================================================================================================================================+
      | id   | String | Indicates the database version ID. Its value is unique.                                                                                                                 |
      +------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name | String | Indicates the database version number. Only the major version number (two digits) is returned. For example, if the version number is MySQL 5.6.X, only 5.6 is returned. |
      +------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "dataStores": [{
              "id": "87620726-6802-46c0-9028-a8785e1f1921",
              "name": "8.0"
          }, {
              "id": "87620726-6802-46c0-9028-a8785e1f1922",
              "name": "5.7"
          }, {
              "id": "e8a8b8cc-63f8-4fb5-8d4a-24c502317a62",
              "name": "5.6"
          }]
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
