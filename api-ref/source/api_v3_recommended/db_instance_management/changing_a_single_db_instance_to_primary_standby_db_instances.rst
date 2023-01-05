:original_name: rds_01_0103.html

.. _rds_01_0103:

Changing a Single DB Instance to Primary/Standby DB Instances
=============================================================

Function
--------

This API is used to change a single DB instance to primary/standby DB instances.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/action

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------+-----------+--------+-------------------------------------------------------------------+
      | Name         | Mandatory | Type   | Description                                                       |
      +==============+===========+========+===================================================================+
      | single_to_ha | Yes       | Object | For details, see :ref:`Table 3 <rds_01_0103__table724844712247>`. |
      +--------------+-----------+--------+-------------------------------------------------------------------+

   .. _rds_01_0103__table724844712247:

   .. table:: **Table 3** single_to_ha field data structure description

      +------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Name             | Mandatory | Type   | Description                                                                                                              |
      +==================+===========+========+==========================================================================================================================+
      | az_code_new_node | Yes       | String | Specifies the AZ code of the DB instance node.                                                                           |
      +------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | password         | No        | String | This parameter is mandatory only when a Microsoft SQL Server DB instance type is changed from single to primary/standby. |
      +------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

-  Example

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/action

-  Request example

   .. code-block:: text

      {
          "single_to_ha": {
              "az_code_new_node": "az2xahz",
              "password": "Test@1234567"
          }
      }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      ====== ====== ======================
      Name   Type   Description
      ====== ====== ======================
      job_id String Indicates the task ID.
      ====== ====== ======================

-  Example normal response

   .. code-block:: text

      {
          "job_id": "2b414788a6004883a02390e2eb0ea227"
      }

-  Abnormal Response

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
