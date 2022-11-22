:original_name: en-us_topic_0056890260.html

.. _en-us_topic_0056890260:

Obtaining a Parameter Template List
===================================

Function
--------

This API is used to obtain a parameter template list, including all databases' default and custom parameter templates.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

-  Restrictions

   Currently, the DB engines MySQL and PostgreSQL support obtaining parameter template lists.

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +----------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Name           | Type                                                                                                | Description                                                                                                                |
      +================+=====================================================================================================+============================================================================================================================+
      | configurations | List data structure. For details, see :ref:`Table 3 <en-us_topic_0056890260__table2172481102534>`.  | Indicates the parameter template list.                                                                                     |
      +----------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | links          | List data structure. For details, see :ref:`Table 4 <en-us_topic_0056890260__table29317924102534>`. | Indicates the link compatible with OpenStack. Currently, this parameter functions as a placeholder.                        |
      +----------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | maxgrouplimit  | Int                                                                                                 | Indicates the maximum quota of custom parameter templates. All DB engines share this quota. Its default value is **1000**. |
      +----------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0056890260__table2172481102534:

   .. table:: **Table 3** configurations field data structure description

      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | Name                   | Type                  | Description                                                                                                                          |
      +========================+=======================+======================================================================================================================================+
      | id                     | String                | Indicates the parameter template ID.                                                                                                 |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | name                   | String                | Indicates the parameter template name.                                                                                               |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | description            | String                | Specifies the parameter template description.                                                                                        |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_version_id   | String                | Indicates the database version ID.                                                                                                   |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_version_name | String                | Indicates the database version name.                                                                                                 |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_name         | String                | Indicates the database name.                                                                                                         |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | created                | String                | Indicates the parameter template creation time in the following format: yyyy-MM-ddTHH:mm:ss.                                         |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | updated                | String                | Indicates the parameter template updated time in the following format: yyyy-MM-ddTHH:mm:ss.                                          |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | allowed_updated        | Int                   | Indicates whether the parameters in the obtained parameter template can be modified.                                                 |
      |                        |                       |                                                                                                                                      |
      |                        |                       | -  **0**: indicates the parameters cannot be modified. When a default parameter template is obtained, this parameter value is **0**. |
      |                        |                       | -  **1**: indicates the parameters can be modified.                                                                                  |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | instance_count         | Int                   | Indicates the number of associated DB instances.                                                                                     |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0056890260__table29317924102534:

   .. table:: **Table 4** links field data structure description

      +------+--------+-------------------------------------------------------------------------------------------------------------------------+
      | Name | Type   | Description                                                                                                             |
      +======+========+=========================================================================================================================+
      | href | String | Indicates the link URL. Currently, this parameter functions as a placeholder and its value is **""**.                   |
      +------+--------+-------------------------------------------------------------------------------------------------------------------------+
      | rel  | String | Indicates the link redirection. Currently, this parameter functions as a placeholder and its default value is **next**. |
      +------+--------+-------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "configurations": [
          {
            "id": "07fc12a8e0e94df7a3fcf53d0b5e1605pr01",
            "name": "default-mysql-5.6",
            "description": "Default parameter group for mysql 5.6",
            "datastore_version_id": "",
            "datastore_version_name": "5.6",
            "datastore_name": "mysql",
            "created": "2017-01-01T10:00:00",
            "updated": "2017-01-01T10:00:00",
            "allowed_updated": 0,
            "instance_count": 0
      },
          {
            "id": "3bc1e9cc0d34404b9225ed7a58fb284epr01",
            "name": "test-mysql-5.6",
            "description": "test-mysql-5.6",
            "datastore_version_id": "",
            "datastore_version_name": "5.6",
            "datastore_name": "mysql",
            "created": "2017-02-01T10:00:00",
            "updated": "2017-02-01T10:00:00",
            "allowed_updated": 1,
            "instance_count": 2
          }
        ],
        "links": [
          {
            "href": "",
            "rel": "next"
          }
        ],
        "maxgrouplimit": 100
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
