:original_name: en-us_topic_0056890053.html

.. _en-us_topic_0056890053:

Obtaining a DB Instance List
============================

Function
--------

This API is used to obtain a DB instance list.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/instances

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

-  Restrictions

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------+-----------------------------------------------------------------------------------------------------+----------------------------------------+
      | Name      | Type                                                                                                | Description                            |
      +===========+=====================================================================================================+========================================+
      | instances | List data structure. For details, see :ref:`Table 4 <en-us_topic_0056890053__table13892167113923>`. | Indicates the DB instance information. |
      +-----------+-----------------------------------------------------------------------------------------------------+----------------------------------------+

   .. table:: **Table 3** instances field data structure description

      +----------+-----------------------------------------------------------------------------------------------------------+----------------------------------------+
      | Name     | Type                                                                                                      | Description                            |
      +==========+===========================================================================================================+========================================+
      | instance | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0056890053__table13892167113923>`. | Indicates the DB instance information. |
      +----------+-----------------------------------------------------------------------------------------------------------+----------------------------------------+

   .. _en-us_topic_0056890053__table13892167113923:

   .. table:: **Table 4** instance field data structure description

      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | Name                  | Type                                                                                                      | Description                                                             |
      +=======================+===========================================================================================================+=========================================================================+
      | status                | String                                                                                                    | Indicates the DB instance status.                                       |
      |                       |                                                                                                           |                                                                         |
      |                       |                                                                                                           | Value:                                                                  |
      |                       |                                                                                                           |                                                                         |
      |                       |                                                                                                           | -  If the value is **BUILD**, the instance is being created.            |
      |                       |                                                                                                           | -  If the value is **ACTIVE**, the instance is normal.                  |
      |                       |                                                                                                           | -  If the value is **FAILED**, the instance is abnormal.                |
      |                       |                                                                                                           | -  If the value is **MODIFYING**, the instance is being scaled up.      |
      |                       |                                                                                                           | -  If the value is **REBOOTING**, the instance is being rebooted.       |
      |                       |                                                                                                           | -  If the value is **RESTORING**, the instance is being restored.       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | name                  | String                                                                                                    | Indicates the DB instance name.                                         |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | links                 | List data structure. For details, see :ref:`Table 5 <en-us_topic_0056890053__table26919596115413>`.       | Indicates the link address.                                             |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | id                    | String                                                                                                    | Indicates the DB instance ID.                                           |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | volume                | Dictionary data structure. For details, see :ref:`Table 6 <en-us_topic_0056890053__table47858865115627>`. | Indicates the volume information.                                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | flavor                | Dictionary data structure. For details, see :ref:`Table 7 <en-us_topic_0056890053__table45121734115759>`. | Indicates the DB instance specifications.                               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | datastore             | Dictionary data structure. For details, see :ref:`Table 8 <en-us_topic_0056890053__table25266871114925>`. | Indicates the database information.                                     |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | region                | String                                                                                                    | Indicates the region where the DB instance is deployed.                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | ip                    | String                                                                                                    | Indicates the DB instance IP address.                                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | replica_of            | Dictionary data structure. For details, see :ref:`Table 9 <en-us_topic_0056890053__table2070063511535>`.  | Indicates the primary DB instance ID corresponding to the read replica. |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
      | hostname              | String                                                                                                    | Indicates the domain name. Its value is **null**.                       |
      |                       |                                                                                                           |                                                                         |
      |                       |                                                                                                           | Currently, this parameter is not supported.                             |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+

   .. _en-us_topic_0056890053__table26919596115413:

   .. table:: **Table 5** links field data structure description

      ==== ====== ======================================
      Name Type   Description
      ==== ====== ======================================
      rel  String Its value is **self** or **bookmark**.
      href String Its value is **""**.
      ==== ====== ======================================

   .. _en-us_topic_0056890053__table47858865115627:

   .. table:: **Table 6** volume field data structure description

      ==== ====== ==========================
      Name Type   Description
      ==== ====== ==========================
      type String Indicates the volume type.
      size Int    Indicates the volume size.
      ==== ====== ==========================

   .. _en-us_topic_0056890053__table45121734115759:

   .. table:: **Table 7** flavor field data structure description

      +-------+-----------------------------------------------------------------------------------------------------+---------------------------------+
      | Name  | Type                                                                                                | Description                     |
      +=======+=====================================================================================================+=================================+
      | id    | String                                                                                              | Indicates the specification ID. |
      +-------+-----------------------------------------------------------------------------------------------------+---------------------------------+
      | links | List data structure. For details, see :ref:`Table 5 <en-us_topic_0056890053__table26919596115413>`. | Indicates the link address.     |
      +-------+-----------------------------------------------------------------------------------------------------+---------------------------------+

   .. _en-us_topic_0056890053__table25266871114925:

   .. table:: **Table 8** datastore field data structure description

      ======= ====== ===============================
      Name    Type   Description
      ======= ====== ===============================
      type    String Indicates the DB engine type.
      version String Indicates the database version.
      ======= ====== ===============================

   .. _en-us_topic_0056890053__table2070063511535:

   .. table:: **Table 9** replica_of field data structure description

      +-------+-----------------------------------------------------------------------------------------------------+---------------------------------------+
      | Name  | Type                                                                                                | Description                           |
      +=======+=====================================================================================================+=======================================+
      | id    | String                                                                                              | Indicates the primary DB instance ID. |
      +-------+-----------------------------------------------------------------------------------------------------+---------------------------------------+
      | links | List data structure. For details, see :ref:`Table 5 <en-us_topic_0056890053__table26919596115413>`. | Indicates the link address.           |
      +-------+-----------------------------------------------------------------------------------------------------+---------------------------------------+

-  Response example

   .. code-block:: text

      {
        "instances": [
          {
            "instance": {
              "status": "ACTIVE",
              "name": "rds-new-channle-read",
              "links": [
                {
                  "rel": "self",
                  "href": ""
                },
                {
                  "rel": "bookmark",
                  "href": ""
                }
              ],
              "id": "37f52707-2fb3-482c-a444-77a70a4eafd6",
              "volume": {
                "type": "COMMON",
                "size": 100
              },
              "flavor": {
                "id": "7fbf27c5-07e5-43dc-cf13-ad7a0f1c5d9a",
                "links": [
                  {
                    "rel": "self",
                    "href": ""
                  },
                  {
                    "rel": "bookmark",
                    "href": ""
                  }
                ]
              },
              "datastore": {
                "type": "PostgreSQL",
                "version": "PostgreSQL-13"
              },

              "region": "eu-de",
              "ip": "192.168.1.29",
              "replica_of": [
                {
                  "id": "c42cdd29-9912-4b57-91a8-c37a845566b1",
                  "links": [
                    {
                      "rel": "self",
                      "href": ""
                    },
                    {
                      "rel": "bookmark",
                      "href": ""
                    }
                  ]
                }
              ],
              "hostname": null
            }
          }
        ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
