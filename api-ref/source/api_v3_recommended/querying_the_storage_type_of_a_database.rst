:original_name: rds_04_0002.html

.. _rds_04_0002:

Querying the Storage Type of a Database
=======================================

Function
--------

This API is used to query the storage type of a specified DB engine version.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/storage-type/{database_name}?version_name={version_name}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                      |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | database_name         | Yes                   | Specifies the DB engine name. Its value can be any of the following and is case-insensitive:                                                                           |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | -  MySQL                                                                                                                                                               |
      |                       |                       | -  PostgreSQL                                                                                                                                                          |
      |                       |                       | -  SQLServer                                                                                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | version_name          | Yes                   | Specifies the database version. For details about how to obtain the database version, see section :ref:`Querying Version Information About a DB Engine <rds_06_0001>`. |
      |                       |                       |                                                                                                                                                                        |
      |                       |                       | -  MySQL databases support 5.6, 5.7, and 8.0.                                                                                                                          |
      |                       |                       | -  PostgreSQL databases support 9.5, 9.6, 10, 11, 12, 13, 14 and 15.                                                                                                   |
      |                       |                       | -  Microsoft SQL Server databases only support 2017_SE, 2017_EE, 2019_SE, 2019_EE, 2022_SE and 2022_EE.                                                                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/storage-type/mysql?version_name=5.7&ha_mode=ha

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | storage_type          | Array of objects      | Indicates the DB instance specifications information list.         |
      |                       |                       |                                                                    |
      |                       |                       | For details, see :ref:`Table 3 <rds_04_0002__table66531170>`.      |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | dsspool_info          | Array of objects      | Indicates the dsspool specifications information list.             |
      |                       |                       |                                                                    |
      |                       |                       | For details, see :ref:`Table 4 <rds_04_0002__table1513533533518>`. |
      |                       |                       |                                                                    |
      |                       |                       | .. note::                                                          |
      |                       |                       |                                                                    |
      |                       |                       |    Only Dedicated Cloud (DeC) users are supported.                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

   .. _rds_04_0002__table66531170:

   .. table:: **Table 3** storage_type field data structure description

      +----------------------------+-----------------------+-------------------------------------------------------------------------------------+
      | Name                       | Type                  | Description                                                                         |
      +============================+=======================+=====================================================================================+
      | name                       | String                | Indicates the storage type. Its value can be any of the following:                  |
      |                            |                       |                                                                                     |
      |                            |                       | -  **COMMON**: SATA storage.                                                        |
      |                            |                       | -  **ULTRAHIGH**: ultra-high I/O storage.                                           |
      |                            |                       | -  **CLOUDSSD**: cloud SSD storage.                                                 |
      |                            |                       | -  **ESSD**: extreme SSD storage.                                                   |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------+
      | az_status                  | Map<String, String>   | Indicates the specification status in an AZ. Its value can be any of the following: |
      |                            |                       |                                                                                     |
      |                            |                       | -  **normal**: indicates that the specifications in the AZ are available.           |
      |                            |                       | -  **unsupported**: indicates that the specifications are not supported by the AZ.  |
      |                            |                       | -  **sellout**: indicates that the specifications in the AZ are sold out.           |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------+
      | support_compute_group_type | List<String>          | Indicates the performance specifications. Its value can be any of the following:    |
      |                            |                       |                                                                                     |
      |                            |                       | -  **normal**: general-enhanced                                                     |
      |                            |                       | -  **general**: general-purpose                                                     |
      |                            |                       | -  **dedicated**                                                                    |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------+

   .. _rds_04_0002__table1513533533518:

   .. table:: **Table 4** dsspool_info field data structure description

      +-----------------------+-----------------------+----------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                          |
      +=======================+=======================+======================================================================+
      | az_name               | String                | Indicates the name of the AZ where dsspool is located.               |
      +-----------------------+-----------------------+----------------------------------------------------------------------+
      | free_capacity_gb      | String                | Indicates the available capacity of dsspool.                         |
      +-----------------------+-----------------------+----------------------------------------------------------------------+
      | dsspool_volume_type   | String                | Indicates the dsspool volume type.                                   |
      +-----------------------+-----------------------+----------------------------------------------------------------------+
      | dsspool_id            | String                | Indicates the dsspool ID.                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------+
      | dsspool_status        | String                | Indicates the dsspool status. Its value can be any of the following: |
      |                       |                       |                                                                      |
      |                       |                       | -  available                                                         |
      |                       |                       | -  deploying                                                         |
      |                       |                       | -  enlarging                                                         |
      |                       |                       | -  frozen                                                            |
      |                       |                       | -  sellout                                                           |
      +-----------------------+-----------------------+----------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "storage_type": [{
                  "name": "COMMON",
                  "az_status": {
                      "az1": "normal",
                      "az2": "normal",
                  },
                              "support_compute_group_type": [
                                      "normal",
                                      "general",
                                      "dedicated"
                              ]
              },
              {
                  "name": "ULTRAHIGH",
                  "az_status": {
                      "az1": "normal",
                      "az2": "normal"
                  },
                              "support_compute_group_type": [
                                      "normal",
                                      "general",
                                      "dedicated"
                              ]
              }
          ]
              "dsspool_info": []
      }

-  Abnormal response

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
