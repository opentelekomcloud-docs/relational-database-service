:original_name: rds_09_0302.html

.. _rds_09_0302:

Creating a Parameter Template
=============================

Function
--------

This API is used to create a parameter template and configure the name, description, DB engine, and parameter values in the parameter template.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

The name of the created parameter template cannot be the same as that of the default or an existing parameter template.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/configurations

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

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================================================+
      | name            | Yes             | String          | Specifies the parameter template name. It contains a maximum of 64 characters and can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.). |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String          | Specifies the parameter template description. It contains a maximum of 256 characters and cannot contain the following special characters: >!<"&'= Its value is left blank by default.          |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values          | No              | Object          | Specifies the parameter values defined by users based on the default parameter template. By default, the parameter values cannot be changed.                                                    |
      |                 |                 |                 |                                                                                                                                                                                                 |
      |                 |                 |                 | For details, see :ref:`Table 3 <rds_09_0302__table766183663313>`.                                                                                                                               |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore       | Yes             | Object          | Specifies the database object.                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                 |
      |                 |                 |                 | For details, see :ref:`Table 4 <rds_09_0302__table1266173643311>`.                                                                                                                              |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0302__table766183663313:

   .. table:: **Table 3** values field data structure description

      +-------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name  | Mandatory | Type   | Description                                                                                                                                                                                                                                               |
      +=======+===========+========+===========================================================================================================================================================================================================================================================+
      | key   | No        | String | Specifies the parameter name. For example, in **"max_connections": "10"**, the key is **max_connections**. If **key** is left blank, the parameter **value** cannot be changed. If **key** is not empty, the parameter **value** cannot be empty, either. |
      +-------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value | No        | String | Specifies the parameter value. For example, in **"max_connections": "10"**, the value is **10**.                                                                                                                                                          |
      +-------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0302__table1266173643311:

   .. table:: **Table 4** datastore field data structure description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                             |
      +=================+=================+=================+=========================================================================================+
      | type            | Yes             | String          | Specifies the DB engine. Its value can be any of the following and is case-insensitive: |
      |                 |                 |                 |                                                                                         |
      |                 |                 |                 | -  MySQL                                                                                |
      |                 |                 |                 | -  PostgreSQL                                                                           |
      |                 |                 |                 | -  SQLServer                                                                            |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------+
      | version         | Yes             | String          | Specifies the database version.                                                         |
      |                 |                 |                 |                                                                                         |
      |                 |                 |                 | Example values:                                                                         |
      |                 |                 |                 |                                                                                         |
      |                 |                 |                 | -  MySQL: **8.0**                                                                       |
      |                 |                 |                 | -  PostgreSQL: **13**                                                                   |
      |                 |                 |                 | -  SQLServer: **2017_SE**                                                               |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------+

-  Example

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/configurations

-  Request example

   .. code-block:: text

      {
          "name": "configuration_test",
          "description": "configuration_test",
          "values": {
              "max_connections": "10",
              "autocommit": "OFF"
          },
          "datastore": {
              "type": "mysql",
              "version": "8.0"
          }
      }

Response
--------

-  Normal response

   .. table:: **Table 5** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | configuration         | Object                | Indicates the parameter template information.                      |
      |                       |                       |                                                                    |
      |                       |                       | For details, see :ref:`Table 6 <rds_09_0302__table1113193619337>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

   .. _rds_09_0302__table1113193619337:

   .. table:: **Table 6** configuration field data structure description

      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                   | Type                  | Description                                                                                                        |
      +========================+=======================+====================================================================================================================+
      | id                     | String                | Indicates the parameter template ID.                                                                               |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                   | String                | Indicates the parameter template name.                                                                             |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_version_name | String                | Indicates the database version name.                                                                               |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_name         | String                | Indicates the database name.                                                                                       |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | description            | String                | Indicates the parameter template description.                                                                      |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created                | String                | Indicates the creation time in the following format: yyyy-MM-ddTHH:mm:ssZ.                                         |
      |                        |                       |                                                                                                                    |
      |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | updated                | String                | Indicates the update time in the following format: yyyy-MM-ddTHH:mm:ssZ.                                           |
      |                        |                       |                                                                                                                    |
      |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "configuration": {
              "id": "463b4b58-d0e8-4e2b-9560-5dea4552fde9",
              "name": "configuration_test",
              "datastore_version_name": "5.6",
              "datastore_name": "mysql",
              "description": "configuration_test",
              "created": "2017-04-09T08:27:56+0800",
              "updated": "2017-04-09T08:27:56+0800"
          }
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
