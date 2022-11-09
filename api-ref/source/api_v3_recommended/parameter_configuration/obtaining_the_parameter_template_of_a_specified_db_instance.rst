:original_name: rds_09_0306.html

.. _rds_09_0306:

Obtaining the Parameter Template of a Specified DB Instance
===========================================================

Function
--------

This API is used to obtain information about the parameter template of a specified DB instance.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The following DB engines are supported: MySQL, PostgreSQL, and Microsoft SQL Server.
-  For Microsoft SQL Server, only the following editions are supported: Microsoft SQL Server 2014 SE, 2016 SE, and 2016 EE.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/configurations

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/configurations

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID compliant with the UUID format.                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

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
      | datastore_version_name   | String                | Indicates the database version name.                                                                               |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_name           | String                | Indicates the database name.                                                                                       |
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
      |                          |                       | For details, see :ref:`Table 3 <rds_09_0306__table19183193052719>`.                                                |
      +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0306__table19183193052719:

   .. table:: **Table 3** configuration_parameters field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                           |
      +=======================+=======================+=======================================================================================================================================================+
      | name                  | String                | Indicates the parameter name.                                                                                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value                 | String                | Indicates the parameter value.                                                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restart_required      | Boolean               | Indicates whether a reboot is required.                                                                                                               |
      |                       |                       |                                                                                                                                                       |
      |                       |                       | -  **false**: A reboot is not required.                                                                                                               |
      |                       |                       | -  **true**: A reboot is required.                                                                                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | readonly              | Boolean               | Indicates whether the parameter is read-only.                                                                                                         |
      |                       |                       |                                                                                                                                                       |
      |                       |                       | -  **false**: The parameter is not read-only.                                                                                                         |
      |                       |                       | -  **true**: The parameter is read-only.                                                                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value_range           | String                | Indicates the parameter value range. If the type is Integer, the value is **0** or **1**. If the type is Boolean, the value is **true** or **false**. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | Indicates the parameter type, which can be **integer**, **string**, **boolean**, **list**, or **float**.                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Indicates the parameter description.                                                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "datastore_version_name": "5.7",
          "datastore_name": "mysql",
          "created": "2018-10-11 11:40:44",
          "updated": "2018-10-11 11:40:44",
          "configuration_parameters": [{
              "name": "auto_increment_increment",
              "value": "1",
              "restart_required": false,
              "readonly": false,
              "value_range": "1-65535",
              "type": "integer",
              "description": auto_increment_increment and auto_increment_offset are used for master-to-master replication and to control the operations of the AUTO_INCREMENT column.
          }]
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
