:original_name: rds_09_0301.html

.. _rds_09_0301:

Obtaining a Parameter Template List
===================================

Function
--------

This API is used to obtain the parameter template list, including default parameter templates of all databases and those created by users.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The following DB engines are supported: MySQL, PostgreSQL, and Microsoft SQL Server.
-  For Microsoft SQL Server, only the following editions are supported: Microsoft SQL Server 2014 SE, 2016 SE, and 2016 EE.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{*project_id*}/configurations

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/configurations

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | configurations        | Array of objects      | Indicates the parameter template list.                             |
      |                       |                       |                                                                    |
      |                       |                       | For details, see :ref:`Table 3 <rds_09_0301__table1324110018258>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

   .. _rds_09_0301__table1324110018258:

   .. table:: **Table 3** configurations field data structure description

      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                   | Type                  | Description                                                                                                        |
      +========================+=======================+====================================================================================================================+
      | id                     | String                | Specifies the parameter template ID.                                                                               |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                   | String                | Indicates the parameter template name.                                                                             |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | description            | String                | Indicates the parameter template description.                                                                      |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_version_name | String                | Indicates the database version name.                                                                               |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_name         | String                | Indicates the database name.                                                                                       |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created                | String                | Indicates the creation time in the following format: yyyy-MM-ddTHH:mm:ssZ.                                         |
      |                        |                       |                                                                                                                    |
      |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | updated                | String                | Indicates the update time in the following format: yyyy-MM-ddTHH:mm:ssZ.                                           |
      |                        |                       |                                                                                                                    |
      |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | user_defined           | Boolean               | Specifies whether the parameter template is created by users.                                                      |
      |                        |                       |                                                                                                                    |
      |                        |                       | -  **false**: The parameter template is a default parameter template.                                              |
      |                        |                       | -  **true**: The parameter template is a custom template.                                                          |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "configurations": [{
                  "id": "887ea0d1bb0843c49e8d8e5a09a95652pr01",
                  "name": "configuration_test",
                  "description": "configuration_test",
                  "datastore_version_name": "5.6",
                  "datastore_name": "mysql",
                  "created": "2019-05-15T11:53:34+0000",
                  "updated": "2019-05-15T11:53:34+0000",
                  "user_defined": true
              },
              {
                  "id": "3bc1e9cc0d34404b9225ed7a58fb284epr01",
                  "name": "Default-MySQL-5.7",
                  "description": "Default parameter group for MySQL 5.7",
                  "datastore_version_name": "5.7",
                  "datastore_name": "mysql",
                  "created": "2019-05-27T03:38:51+0000",
                  "updated": "2019-05-27T03:38:51+0000",
                  "user_defined": false
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
