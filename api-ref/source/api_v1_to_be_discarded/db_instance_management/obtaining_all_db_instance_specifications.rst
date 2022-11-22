:original_name: en-us_topic_0032347783.html

.. _en-us_topic_0032347783:

Obtaining All DB Instance Specifications
========================================

Function
--------

This API is used to obtain all instance specifications of a specified database version ID in a specified region.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/flavors

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Request
-------

-  Parameter description

   .. _en-us_topic_0032347783__table50945089161848:

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                |
      +=======================+=======================+============================================================================================================================================================================+
      | dbId                  | Yes                   | Specifies the database version ID (**dataStores.id** in the response message in :ref:`Database Version Queries <en-us_topic_0032347782>`).                                 |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | Valid value: The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | Yes                   | Specifies the region where the DB instance is deployed.                                                                                                                    |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | Valid value:                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | The value cannot be empty. For details about how to obtain this parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      /rds/v1/375d8d8fad1f43039e23d3b6c0f60a19/flavors?dbId=e8a8b8cc-63f8-4fb5-8d4a-24c502317a6&region=eu-de

Normal Response
---------------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +---------+-----------------------------------------------------------------------------------------------+------------------------------------------------------------+
      | Name    | Type                                                                                          | Description                                                |
      +=========+===============================================================================================+============================================================+
      | flavors | List data structure. For details, see :ref:`Table 4 <en-us_topic_0032347783__table34207804>`. | Indicates the DB instance specifications information list. |
      +---------+-----------------------------------------------------------------------------------------------+------------------------------------------------------------+

   .. _en-us_topic_0032347783__table34207804:

   .. table:: **Table 4** flavors field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================+
      | id                    | String                | Indicates the specification ID. Its value is unique.                                                                                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the specification item name.                                                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | ram                   | Int                   | Indicates the memory size in megabytes (MB).                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | specCode              | String                | Indicates the resource specification code.                                                                                          |
      |                       |                       |                                                                                                                                     |
      |                       |                       | Use **rds.mysql.m1.xlarge** as an example.                                                                                          |
      |                       |                       |                                                                                                                                     |
      |                       |                       | **rds** indicates RDS, **mysql** indicates the DB engine, and **m1.xlarge** indicates the performance specification (large-memory). |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "flavors": [
              {
                  "id": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4",
                  "name": "OTC_MYHP_LARGE",
                  "ram": 4096,
                  "specCode": "rds.mysql.c2.large"
              },
              {
                  "id": "f7f51f85-cfcd-4409-ae91-b3eae186d0ea",
                  "name": "OTC_MYLM_XLARGE",
                  "ram": 32768,
                  "specCode": "rds.mysql.m1.xlarge"
              }
          ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
