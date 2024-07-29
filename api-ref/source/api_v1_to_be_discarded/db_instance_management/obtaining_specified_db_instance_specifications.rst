:original_name: en-us_topic_0032347784.html

.. _en-us_topic_0032347784:

Obtaining Specified DB Instance Specifications
==============================================

Function
--------

This API is used to obtain DB instance specifications of a specified specification ID.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/flavors/{flavorId}

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavorId              | Yes                   | Specifies the specification ID compliant with the UUID format.                                                                                                                |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | For details about how to obtain this parameter value, see **flavors.id** in the response message in :ref:`Obtaining All DB Instance Specifications <en-us_topic_0032347783>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+-----------------------------------------------------------------------------------------------+------------------------------------------------------------+
      | Name   | Type                                                                                          | Description                                                |
      +========+===============================================================================================+============================================================+
      | flavor | List data structure. For details, see :ref:`Table 3 <en-us_topic_0032347784__table64140254>`. | Indicates the DB instance specifications information list. |
      +--------+-----------------------------------------------------------------------------------------------+------------------------------------------------------------+

   .. _en-us_topic_0032347784__table64140254:

   .. table:: **Table 3** flavor field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================+
      | id                    | String                | Indicates the specification ID. Its value is unique.                                                                                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the specification item name.                                                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | ram                   | Int                   | Indicates the memory size in megabytes (MB).                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | specCode              | String                | Indicates the resource specifications code.                                                                                         |
      |                       |                       |                                                                                                                                     |
      |                       |                       | Use **rds.mysql.n1.xlarge** as an example.                                                                                          |
      |                       |                       |                                                                                                                                     |
      |                       |                       | **rds** indicates RDS, **mysql** indicates the DB engine, and **n1.xlarge** indicates the performance specification (large-memory). |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "flavor": {
              "id": "f7f51f85-cfcd-4409-ae91-b3eae186d0ea",
              "name": "OTC_MYLM_XLARGE",
              "ram": 32768,
              "specCode": "rds.mysql.n1.xlarge"
          }
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
