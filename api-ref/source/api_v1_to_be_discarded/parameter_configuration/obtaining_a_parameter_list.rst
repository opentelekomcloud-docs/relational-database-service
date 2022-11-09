:original_name: en-us_topic_0034943369.html

.. _en-us_topic_0034943369:

Obtaining a Parameter List
==========================

Function
--------

This API is used to obtain all the parameters that can be modified of the current database version.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/datastores/versions/{datastore_version_id}/parameters

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

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
      | Name                     | Type                                                                                          | Description                                                                |
      +==========================+===============================================================================================+============================================================================+
      | configuration-parameters | List data structure. For details, see :ref:`Table 3 <en-us_topic_0034943369__table34207804>`. | Indicates all the parameters that can be modified of the database version. |
      +--------------------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

   .. _en-us_topic_0034943369__table34207804:

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
      | type                 | String  | Indicates the parameter type. The value can be **integer**, **string**, **boolean**, **float**, or **list**.         |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | value_range          | String  | Specifies the parameter value range and enumerated value.                                                            |
      +----------------------+---------+----------------------------------------------------------------------------------------------------------------------+
      | description          | String  | Indicates the parameter description.                                                                                 |
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
          "value_range" : "ON|OFF",
          "description" : "The autocommit mode. If set to ON, all changes to a table take effect immediately. If set to OFF, you must use COMMIT to accept a transaction or ROLLBACK to cancel it. ",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "auto_increment_increment",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "value_range": "1-65535",
          "description" : "auto_increment_increment and auto_increment_offset are intended for use with master-to-master replication, and can be used to control the operation of AUTO_INCREMENT columns.",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "auto_increment_offset",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "value_range": "1-65535",
          "description" : "auto_increment_increment and auto_increment_offset are intended for use with master-to-master replication, and can be used to control the operation of AUTO_INCREMENT columns. ",
          "restart_required" : false,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
        }, {
          "name" : "back_log",
          "min" : "1",
          "max" : "65535",
          "type" : "integer",
          "value_range": "1-65535",
          "description" : "The number of outstanding connection requests MySQL can have. This comes into play when the main MySQL thread gets very many connection requests in a very short time. It then takes some time (although very little) for the main thread to check the connection and start a new thread. The back_log value indicates how many requests can be stacked during this short time before MySQL momentarily stops answering new requests. The default value depends on system architecture.",
          "restart_required" : true,
          "datastore_version_id" : "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61"
          }
        ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
