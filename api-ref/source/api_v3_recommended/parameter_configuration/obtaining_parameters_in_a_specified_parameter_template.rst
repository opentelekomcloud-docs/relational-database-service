:original_name: rds_09_0307.html

.. _rds_09_0307:

Obtaining Parameters in a Specified Parameter Template
======================================================

Function
--------

This API is used to obtain parameters of a specified parameter template.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The following DB engines are supported: MySQL, PostgreSQL, and Microsoft SQL Server.
-  For Microsoft SQL Server, only the following editions are supported: Microsoft SQL Server 2014 SE, 2016 SE, and 2016 EE.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/configurations/{config_id}

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/configurations/463b4b58-d0e8-4e2b-9560-5dea4552fde9

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                              |
      +=======================+=======================+==========================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                        |
      |                       |                       |                                                                                                                                                                          |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | config_id             | Yes                   | Specifies the parameter template ID.                                                                                                                                     |
      |                       |                       |                                                                                                                                                                          |
      |                       |                       | When this parameter is empty (not space), the URL of the parameter template list is obtained. For details, see :ref:`Obtaining a Parameter Template List <rds_09_0301>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                     | Type                  | Description                                                                                                        |
      +==========================+=======================+====================================================================================================================+
      | id                       | String                | Indicates the parameter template ID.                                                                               |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                     | String                | Indicates the parameter template name.                                                                             |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_version_name   | String                | Indicates the database version name.                                                                               |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_name           | String                | Indicates the database name.                                                                                       |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | description              | String                | Indicates the parameter template description.                                                                      |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created                  | String                | Indicates the creation time in the following format: yyyy-MM-ddTHH:mm:ssZ.                                         |
      |                          |                       |                                                                                                                    |
      |                          |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | updated                  | String                | Indicates the update time in the following format: yyyy-MM-ddTHH:mm:ssZ.                                           |
      |                          |                       |                                                                                                                    |
      |                          |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | configuration_parameters | Array of objects      | Indicates the parameters defined by users based on the default parameter templates.                                |
      |                          |                       |                                                                                                                    |
      |                          |                       | For details, see :ref:`Table 3 <rds_09_0307__table082923016312>`.                                                  |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0307__table082923016312:

   .. table:: **Table 3** configuration_parameters field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                               |
      +=======================+=======================+===========================================================================================================================================+
      | name                  | String                | Indicates the parameter name.                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | value                 | String                | Indicates the parameter value.                                                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | restart_required      | Boolean               | Indicates whether a restart is required.                                                                                                  |
      |                       |                       |                                                                                                                                           |
      |                       |                       | -  **false** indicates that a restart is not required.                                                                                    |
      |                       |                       | -  **true** indicates that a restart is required.                                                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | readonly              | Boolean               | Indicates whether the parameter is read-only.                                                                                             |
      |                       |                       |                                                                                                                                           |
      |                       |                       | -  **false**: The parameter is not read-only.                                                                                             |
      |                       |                       | -  **true**: The parameter is read-only.                                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | value_range           | String                | Indicates the parameter value range. For example, the value of **integer** is 0-1, and the value of **boolean** is **true** or **false**. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | Indicates the parameter type, which can be **integer**, **string**, **boolean**, **list**, or **float**.                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Indicates the parameter description.                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "id": "07fc12a8e0e94df7a3fcf53d0b5e1605pr01",
          "name": "default-mysql-5.6",
          "datastore_version_name": "5.6",
          "datastore_name": "mysql",
          "description": "Default parameter group for mysql 5.6",
          "created": "2017-05-05T04:40:51+0800",
          "updated": "2017-05-05T04:40:51+0800",
          "configuration_parameters": [
            {
              "name": "auto_increment_increment",
              "value": "1",
              "restart_required": false,
              "readonly": true,
              "value_range": "1-65535",
              "type": "integer",
              "description": "auto_increment_increment and auto_increment_offset are intended for use with master-to-master replication, and can be used to control the operation of AUTO_INCREMENT columns."
            },
            {
              "name": "autocommit",
              "value": "ON",
              "restart_required": false,
              "readonly": true,
              "value_range": "ON|OFF",
              "type": "boolean",
              "description": "The autocommit mode. If set to ON, all changes to a table take effect immediately. If set to OFF, you must use COMMIT to accept a transaction or ROLLBACK to cancel it. "
            }
          ]
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
