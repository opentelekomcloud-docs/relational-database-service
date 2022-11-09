:original_name: en-us_topic_0032347782.html

.. _en-us_topic_0032347782:

Database Version Queries
========================

Function
--------

This API is used to obtain version information about a specified type of a database.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/datastores/{datastore_name}/versions

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------+
      | Name                  | Mandatory             | Description                                       |
      +=======================+=======================+===================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region. |
      +-----------------------+-----------------------+---------------------------------------------------+
      | datastore_name        | Yes                   | Specifies the DB engine. Valid value:             |
      |                       |                       |                                                   |
      |                       |                       | -  MySQL                                          |
      |                       |                       | -  PostgreSQL                                     |
      |                       |                       | -  SQLServer                                      |
      +-----------------------+-----------------------+---------------------------------------------------+

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +------------+-----------------------------------------------------------------------------------------------+------------------------------------------+
      | Name       | Type                                                                                          | Description                              |
      +============+===============================================================================================+==========================================+
      | dataStores | List data structure. For details, see :ref:`Table 3 <en-us_topic_0032347782__table66531170>`. | Indicates the list of database versions. |
      +------------+-----------------------------------------------------------------------------------------------+------------------------------------------+

   .. _en-us_topic_0032347782__table66531170:

   .. table:: **Table 3** dataStores field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                           |
      +=======================+=======================+=======================================================================================================================+
      | id                    | String                | Indicates the database version ID. Its value is unique.                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the database version.                                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | datastore             | String                | Indicates the database ID.                                                                                            |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | image                 | String                | Indicates the database image ID.                                                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | packages              | String                | Indicates the database package version information.                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | active                | Int                   | Indicates the database version activation status. The API returns information only about activated database versions. |
      |                       |                       |                                                                                                                       |
      |                       |                       | -  **0**: The database version is not activated.                                                                      |
      |                       |                       | -  **1**: The database version is activated.                                                                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "dataStores": [
          {
            "id": "e8a8b8cc-63f8-4fb5-8d4a-24c502317a62",
            "name": "5.6.33",
            "datastore": "736270b9-27c7-4f03-823b-447d8245e1c2",
            "image": "36bdc308-0389-4830-8813-4a98d62b97de",
            "packages": "MySQL-server-5.6.33",
            "active": 1
          },
          {
            "id": "e8a8b8cc-63f8-4fb5-8d4a-24c502317a61",
            "name": "5.6.30",
            "datastore": "736270b9-27c7-4f03-823b-447d8245e1c2",
            "image": "36bdc308-0389-4830-8813-4a98d62b97de",
            "packages": "MySQL-server-5.6.30",
            "active": 1
          },
          {
            "id": "96cccede-bc51-11e6-bd4d-286ed488dd62",
            "name": "5.6.34",
            "datastore": "736270b9-27c7-4f03-823b-447d8245e1c2",
            "image": "36bdc308-0389-4830-8813-4a98d62b97de",
            "packages": "MySQL-server-5.6.34",
            "active": 1
          },
          {
            "id": "35a3d5ba-6f74-4b29-824d-6de20f1ac090",
            "name": "5.6.35",
            "datastore": "736270b9-27c7-4f03-823b-447d8245e1c2",
            "image": "36bdc308-0389-4830-8813-4a98d62b97de",
            "packages": "MySQL-server-5.6.35",
            "active": 1
          },
          {
            "id": "129a90a5-d4ef-4828-b3e3-4d3a1e91700d",
            "name": "5.6.36",
            "datastore": "736270b9-27c7-4f03-823b-447d8245e1c2",
            "image": "36bdc308-0389-4830-8813-4a98d62b97de",
            "packages": "MySQL-server-5.6.36",
            "active": 1
          },
          {
            "id": "87620726-6802-46c0-9028-a8785e1f1922",
            "name": "5.7.17",
            "datastore": "736270b9-27c7-4f03-823b-447d8245e1c2",
            "image": "36bdc308-0389-4830-8813-4a98d62b97de",
            "packages": "MySQL-server-5.7.17",
            "active": 1
          }
        ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
