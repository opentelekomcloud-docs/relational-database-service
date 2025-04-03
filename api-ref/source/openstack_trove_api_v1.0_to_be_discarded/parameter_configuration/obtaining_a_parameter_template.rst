:original_name: en-us_topic_0056890261.html

.. _en-us_topic_0056890261:

Obtaining a Parameter Template
==============================

Function
--------

This API is used to obtain information about a specified parameter template.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations/{id}

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id                    | Yes                   | Indicates the parameter template ID.                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                     |
      |                       |                       | When this parameter is empty (not space), the URL of the parameter template list is obtained. For details, see :ref:`Obtaining a Parameter Template List <en-us_topic_0056890260>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Restrictions

   Currently, the DB engines MySQL and PostgreSQL support obtaining parameter templates.

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +---------------+----------------------------------------------------------------------------------------------------+-----------------------------------+
      | Name          | Type                                                                                               | Description                       |
      +===============+====================================================================================================+===================================+
      | configuration | List data structure. For details, see :ref:`Table 3 <en-us_topic_0056890261__table1092492102747>`. | Indicates the parameter template. |
      +---------------+----------------------------------------------------------------------------------------------------+-----------------------------------+

   .. _en-us_topic_0056890261__table1092492102747:

   .. table:: **Table 3** configuration field data structure description

      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | Name                   | Type                                                                                                      | Description                                                                                   |
      +========================+===========================================================================================================+===============================================================================================+
      | id                     | String                                                                                                    | Indicates the parameter template ID.                                                          |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | name                   | String                                                                                                    | Indicates the parameter template name.                                                        |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | datastore_version_id   | String                                                                                                    | Indicates the database version ID.                                                            |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | datastore_version_name | String                                                                                                    | Indicates the database version name.                                                          |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | datastore_name         | String                                                                                                    | Indicates the database name.                                                                  |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | description            | String                                                                                                    | Indicates the parameter template description.                                                 |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | instance_count         | Int                                                                                                       | Indicates the number of associated DB instances.                                              |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | created                | String                                                                                                    | Indicates the parameter template creation time in the following format: yyyy-MM-dd THH:mm:ss. |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | updated                | String                                                                                                    | Indicates the parameter template updated time in the following format: yyyy-MM-dd THH:mm:ss.  |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | values                 | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0056890261__table24714908102747>`. | Indicates the parameter values defined by users based on the default parameter template.      |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
      | parameters             | List data structure. For details, see :ref:`Table 5 <en-us_topic_0056890261__table42519518102747>`.       | Indicates the parameter list.                                                                 |
      +------------------------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+

   .. _en-us_topic_0056890261__table24714908102747:

   .. table:: **Table 4** values field data structure description

      +-------+--------+---------------------------------------------------------------------------------------------------+
      | Name  | Type   | Description                                                                                       |
      +=======+========+===================================================================================================+
      | key   | String | Indicates the parameter name. For example, in **"xp_cmdshell": "0"**, the key is **xp_cmdshell**. |
      +-------+--------+---------------------------------------------------------------------------------------------------+
      | value | String | Indicates the parameter value. For example, in **"xp_cmdshell": "0"**, the value is **0**.        |
      +-------+--------+---------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0056890261__table42519518102747:

   .. table:: **Table 5** parameters field data structure description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                              |
      +=======================+=======================+==========================================================================================================+
      | name                  | String                | Indicates the parameter name.                                                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
      | value                 | String                | Indicates the value.                                                                                     |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
      | needRestart           | String                | Indicates whether the DB instance needs to be rebooted.                                                  |
      |                       |                       |                                                                                                          |
      |                       |                       | -  **0** indicates that the DB instance does not need to be rebooted.                                    |
      |                       |                       | -  **1** indicates that the DB instance needs to be rebooted.                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
      | readonly              | String                | Indicates whether the parameter template is read-only.                                                   |
      |                       |                       |                                                                                                          |
      |                       |                       | -  **0** indicates that the parameter template is not read-only.                                         |
      |                       |                       | -  **1** indicates that the parameter template is read-only.                                             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
      | valueRange            | String                | Indicates the value range, such as 0-1.                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
      | datatype              | String                | Indicates the parameter type, which can be **integer**, **string**, **boolean**, **list**, or **float**. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
      | description           | String                | Indicates the descriptions of parameters.                                                                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "configuration": {
          "id": "07fc12a8e0e94df7a3fcf53d0b5e1605pr01",
          "name": "default-mysql-5.7",
          "datastore_version_id": "",
          "datastore_version_name": "5.7",
          "datastore_name": "mysql",
          "description": "Default parameter group for mysql 5.7",
          "instance_count": 0,
          "created": "2017-05-05T04:40:51",
          "updated": "2017-05-05T04:40:51",
      "values": {
            "autocommit": "ON"
          },
          "parameters": [
            {
              "name": "auto_increment_increment",
              "value": "1",
              "needRestart": "0",
              "readonly": "1",
              "valueRange": "1-65535",
              "datatype": "integer",
              "description": "auto_increment_increment and auto_increment_offset are intended for use with master-to-master replication, and can be used to control the operation of AUTO_INCREMENT columns."
            },
            {
              "name": "autocommit",
              "value": "ON",
              "needRestart": "0",
              "readonly": "1",
              "valueRange": "ON|OFF",
              "datatype": "boolean",
              "description": "The autocommit mode. If set to ON, all changes to a table take effect immediately. If set to OFF, you must use COMMIT to accept a transaction or ROLLBACK to cancel it. "
            }
          ]
        }
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
