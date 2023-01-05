:original_name: rds_01_0101.html

.. _rds_01_0101:

Changing DB Instance Specifications
===================================

Function
--------

This API is used to change DB instance specifications.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

.. note::

   Services will be interrupted for 5 to 10 minutes when you change DB instance specifications. Exercise caution when performing this operation.

Constraints
-----------

-  The new DB instance specifications must be different from the original DB instance specifications.
-  The instance class can be modified only for DB instances whose status is **Available**.
-  The specifications of a DB instance can be changed only to the specifications of the same DB instance type. (For example, the specifications of a single DB instance cannot be changed to those of primary/standby DB instances.)

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/action

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

      +---------------+-----------+--------+------------------------------------------------------------------+
      | Name          | Mandatory | Type   | Description                                                      |
      +===============+===========+========+==================================================================+
      | resize_flavor | Yes       | Object | For details, see :ref:`Table 3 <rds_01_0101__table68501959278>`. |
      +---------------+-----------+--------+------------------------------------------------------------------+

   .. _rds_01_0101__table68501959278:

   .. table:: **Table 3** resize_flavor field data structure description

      +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name      | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                  |
      +===========+===========+========+==============================================================================================================================================================================================================================================================================================================================================================================================================+
      | spec_code | Yes       | String | Specifies the resource specification code. Use **rds.mysql.m1.xlarge** as an example. **rds** indicates RDS, **mysql** indicates the DB engine, and **m1.xlarge** indicates the performance specification (large-memory). The parameter containing **rr** indicates the read replica specifications. The parameter not containing **rr** indicates the single or primary/standby DB instance specifications. |
      +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/action

-  Request example

   .. code-block:: text

      {
          "resize_flavor": {
              "spec_code": "rds.pg.c2.medium"
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

   202

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
