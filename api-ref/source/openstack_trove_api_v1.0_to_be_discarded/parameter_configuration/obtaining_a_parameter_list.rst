:original_name: en-us_topic_0056890257.html

.. _en-us_topic_0056890257:

Obtaining a Parameter List
==========================

Function
--------

This API is used to obtain all the parameters that can be modified of the current database version.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/datastores/versions/{datastore_version_id}/parameters

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
      | configuration-parameters | List data structure. For details, see :ref:`Table 3 <en-us_topic_0056890257__table31447783102154>`. | Indicates all the parameters that can be modified of the database version. |
      +--------------------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

   .. _en-us_topic_0056890257__table31447783102154:

   .. table:: **Table 3** configuration-parameters field data structure description

      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | Name                 | Type    | Description                                                                                                          |
      +======================+=========+======================================================================================================================+
      | name                 | String  | Indicates the parameter name.                                                                                        |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | min                  | String  | Indicates the minimum value. Returned only when **type** is **integer** or **float**.                                |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | max                  | String  | Indicates the maximum value. Returned only when **type** is **integer** or **float**.                                |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | type                 | String  | Indicates the parameter type, which can be **integer**, **string**, **boolean**, **list**, or **float**.             |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | restart_required     | Boolean | Indicates whether the instance needs to reboot for the parameter to take effect. The value is **true** or **false**. |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | datastore_version_id | String  | Indicates the database version ID.                                                                                   |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "configuration-parameters" : [ {
          "name" : "autocommit",
          "type" : "boolean",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "auto_increment_increment",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "auto_increment_offset",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "back_log",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "restart_required" : true,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
          } ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
