:original_name: en-us_topic_0056890258.html

.. _en-us_topic_0056890258:

Obtaining Information About Configuration Parameters
====================================================

Function
--------

This API is used to obtain information about parameters that can be modified of a specified database version.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/datastores/versions/{datastore_version_id}/parameters/{parameter_name}

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +----------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                 | Mandatory | Description                                                                                                                                |
      +======================+===========+============================================================================================================================================+
      | project_id           | Yes       | Specifies the project ID of a tenant in a region.                                                                                          |
      +----------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_version_id | Yes       | Specifies the database version ID (**dataStores.id** in the response message in :ref:`Database Version Queries <en-us_topic_0032347782>`). |
      +----------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | parameter_name       | Yes       | Specifies the parameter name.                                                                                                              |
      +----------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------+

-  Restrictions

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
      | Name                     | Type                                                                                                | Description                                                                |
      +==========================+=====================================================================================================+============================================================================+
      | configuration-parameters | List data structure. For details, see :ref:`Table 3 <en-us_topic_0056890258__table29072240102314>`. | Indicates all the parameters that can be modified of the database version. |
      +--------------------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

   .. _en-us_topic_0056890258__table29072240102314:

   .. table:: **Table 3** configuration-parameters field data structure description

      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | Name                 | Type    | Description                                                                                                          |
      +======================+=========+======================================================================================================================+
      | name                 | String  | Indicates the parameter name.                                                                                        |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | type                 | String  | Indicates the parameter type, which can be **integer**, **string**, **boolean**, **list**, or **float**.             |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | max                  | String  | Indicates the maximum value of the parameter. Returned only when **type** is **integer** or **float**.               |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | min                  | String  | Indicates the minimum value of the parameter. Returned only when **type** is **integer** or **float**.               |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | datastore_version_id | String  | Indicates the database version ID.                                                                                   |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | restart_required     | Boolean | Indicates whether the instance needs to reboot for the parameter to take effect. The value is **true** or **false**. |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
      "configuration-parameters": [
       {
         "name": "connect_timeout",
         "type": "integer",
         "max": "31536000",
         "min": "2",
         "datastore_version_id": "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61",
         "restart_required": "false"
        }
       ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
