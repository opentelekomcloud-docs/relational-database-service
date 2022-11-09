:original_name: rds_06_0002.html

.. _rds_06_0002:

Querying Database Specifications
================================

Function
--------

This API is used to query the database specifications of a specified DB engine version.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/flavors/{database_name}?version_name={version_name}

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/flavors/mysql?version_name=5.7

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                     |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | database_name         | Yes                   | Specifies the DB engine name. Its value can be any of the following and is case-insensitive:                                                                                        |
      |                       |                       |                                                                                                                                                                                     |
      |                       |                       | -  MySQL                                                                                                                                                                            |
      |                       |                       | -  PostgreSQL                                                                                                                                                                       |
      |                       |                       | -  SQLServer                                                                                                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | version_name          | No                    | Specifies the database version. For details about how to obtain the database version, see section :ref:`Querying Version Information About a DB Engine <rds_06_0001>`.              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code             | No                    | Specifies the specification code.                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                     |
      |                       |                       | .. important::                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                     |
      |                       |                       |    NOTICE:                                                                                                                                                                          |
      |                       |                       |    Only DB instances running Microsoft SQL Server 2017 EE support the creation of read replicas. Microsoft SQL Server 2017 EE does not support the creation of single DB instances. |
      |                       |                       |                                                                                                                                                                                     |
      |                       |                       | The format of the specification code is: {*spec code*}{*instance mode*}.                                                                                                            |
      |                       |                       |                                                                                                                                                                                     |
      |                       |                       | -  *spec code* can be obtained from :ref:`Table 1 <rds_10_0004__ted9b9d433c8a4c52884e199e17f94479>`.                                                                                |
      |                       |                       | -  *instance mode* can be any of the following:                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                     |
      |                       |                       |    -  For single DB instances, the value is **null**. Example spe_code: rds.mysql.s1.xlarge                                                                                         |
      |                       |                       |    -  For primary/standby DB instances, the value is **.ha**. Example spe_code: rds.mysql.s1.xlarge.ha                                                                              |
      |                       |                       |    -  For read replicas, the value is **.rr**. Example spe_code: rds.mysql.s1.xlarge.rr                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------+
      | Name                  | Type                  | Description                                                   |
      +=======================+=======================+===============================================================+
      | flavors               | Array of objects      | Indicates the DB instance specifications information list.    |
      |                       |                       |                                                               |
      |                       |                       | For details, see :ref:`Table 3 <rds_06_0002__table66531170>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------+

   .. _rds_06_0002__table66531170:

   .. table:: **Table 3** flavors field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                           |
      +=======================+=======================+=======================================================================================================================+
      | vcpus                 | String                | Indicates the CPU size. For example, the value **1** indicates 1 vCPU.                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | ram                   | Integer               | Indicates the memory size in GB.                                                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | spec_code             | String                | Indicates the resource specification code. Use **rds.mysql.m1.xlarge.rr** as an example.                              |
      |                       |                       |                                                                                                                       |
      |                       |                       | -  **rds**: indicates the RDS product.                                                                                |
      |                       |                       | -  **mysql**: indicates the DB engine.                                                                                |
      |                       |                       | -  **m1.xlarge**: indicates the high memory performance specifications.                                               |
      |                       |                       | -  **rr**: indicates the read replica (**.ha** indicates primary/standby DB instances).                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | instance_mode         | String                | Indicates the DB instance type. Its value can be any of the following:                                                |
      |                       |                       |                                                                                                                       |
      |                       |                       | -  **ha**: indicates primary/standby DB instances.                                                                    |
      |                       |                       | -  **replica**: indicates read replicas.                                                                              |
      |                       |                       | -  **single**: indicates single DB instances.                                                                         |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | az_status             | Map<String, String>   | Indicates the status of the AZ to which the DB instance specifications belong. Its value can be any of the following: |
      |                       |                       |                                                                                                                       |
      |                       |                       | -  **normal**: indicates that the AZ is on sale.                                                                      |
      |                       |                       | -  **unsupported**: indicates that the DB instance specifications are not supported by the AZ.                        |
      |                       |                       | -  **sellout**: indicates that the DB instance specifications are sold out.                                           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "flavors": [{
              "vcpus": "1",
              "ram": 2,
              "spec_code": "rds.mysql.c2.medium.ha",
              "instance_mode": "ha",
              "az_status": {
                  "az1": "normal",
                  "az2": "normal"
              }
          }, {
              "vcpus": "1",
              "ram": 2,
              "spec_code": "rds.mysql.c2.medium.rr",
              "instance_mode": "replica",
              "az_status": {
                  "az1": "normal",
                  "az2": "normal"
              }
          }]
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
