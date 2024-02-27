:original_name: rds_06_0002.html

.. _rds_06_0002:

Querying Database Specifications
================================

Function
--------

This API is used to query the database specifications of a specified DB engine version.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/flavors/{database_name}?version_name={version_name}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                                                                                                        |
      +=======================+=======================+====================================================================================================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                                                    |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                                                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | database_name         | Yes                   | Specifies the DB engine name. Its value can be any of the following and is case-insensitive:                                                                                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                                                                    |
      |                       |                       | -  MySQL                                                                                                                                                                                                                                                           |
      |                       |                       | -  PostgreSQL                                                                                                                                                                                                                                                      |
      |                       |                       | -  SQLServer                                                                                                                                                                                                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | version_name          | No                    | Specifies the database version. For details about how to obtain the database version, see section :ref:`Querying Version Information About a DB Engine <rds_06_0001>`. For details about the version, see :ref:`DB Engines and Versions <en-us_topic_0043898356>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code             | No                    | Specifies the specification code.                                                                                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                                                    |
      |                       |                       | .. important::                                                                                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                                                    |
      |                       |                       |    NOTICE:                                                                                                                                                                                                                                                         |
      |                       |                       |    For Microsoft SQL Server, Only 2022_EE, 2019_EE and 2017_EE support the creation of read replicas and do not support the creation of single DB instances.                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                                                                    |
      |                       |                       | The format of the specification code is: {*spec code*}{*instance mode*}.                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                                                    |
      |                       |                       | -  *spec code* can be obtained from :ref:`Table 1 <rds_10_0004__table1629815381417>`.                                                                                                                                                                              |
      |                       |                       | -  *instance mode* can be any of the following:                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                    |
      |                       |                       |    -  For single DB instances, the value is **null**. Example spe_code: rds.mysql.s1.xlarge                                                                                                                                                                        |
      |                       |                       |    -  For primary/standby DB instances, the value is **.ha**. Example spe_code: rds.mysql.s1.xlarge.ha                                                                                                                                                             |
      |                       |                       |    -  For read replicas, the value is **.rr**. Example spe_code: rds.mysql.s1.xlarge.rr                                                                                                                                                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/flavors/mysql?version_name=5.7

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | flavors               | Array of objects      | Indicates the DB instance specifications information list.         |
      |                       |                       |                                                                    |
      |                       |                       | For details, see :ref:`Table 3 <rds_06_0002__table1336414511696>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

   .. _rds_06_0002__table1336414511696:

   .. table:: **Table 3** flavors field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                             |
      +=======================+=======================+=========================================================================================================+
      | vcpus                 | String                | Indicates the CPU size. For example, the value **1** indicates 1 vCPU.                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | ram                   | Integer               | Indicates the memory size in GB.                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | id                    | String                | Indicates the specification ID, which is unique.                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | spec_code             | String                | Indicates the resource specification code. Use **rds.mysql.m1.xlarge.rr** as an example.                |
      |                       |                       |                                                                                                         |
      |                       |                       | -  **rds**: indicates the RDS product.                                                                  |
      |                       |                       | -  **mysql**: indicates the DB engine.                                                                  |
      |                       |                       | -  **m1.xlarge**: indicates the high memory performance specifications.                                 |
      |                       |                       | -  **rr**: indicates the read replica (**.ha** indicates primary/standby DB instances).                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | version_name          | Array                 | Indicates the database version.                                                                         |
      |                       |                       |                                                                                                         |
      |                       |                       | -  MySQL databases support 5.6, 5.7, and 8.0.                                                           |
      |                       |                       | -  PostgreSQL databases support 9.5, 9.6, 10, 11, 12, 13, 14, and 15.                                   |
      |                       |                       | -  Microsoft SQL Server databases only support 2017_SE, 2017_EE, 2019_SE, 2019_EE, 2022_SE and 2022_EE. |
      |                       |                       |                                                                                                         |
      |                       |                       | Example value for MySQL: ["5.6","5.7","8.0"]                                                            |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | instance_mode         | String                | Indicates the DB instance type. Its value can be any of the following:                                  |
      |                       |                       |                                                                                                         |
      |                       |                       | -  **ha**: indicates primary/standby DB instances.                                                      |
      |                       |                       | -  **replica**: indicates read replicas.                                                                |
      |                       |                       | -  **single**: indicates single DB instances.                                                           |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | az_status             | Map<String, String>   | Indicates the specification status in an AZ. Its value can be any of the following:                     |
      |                       |                       |                                                                                                         |
      |                       |                       | -  **normal**: indicates that the specifications in the AZ are available.                               |
      |                       |                       | -  **unsupported**: indicates that the specifications are not supported by the AZ.                      |
      |                       |                       | -  **sellout**: indicates that the specifications in the AZ are sold out.                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | az_desc               | Map<String, String>   | Indicates the description of the AZ to which the specifications belong.                                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | group_type            | String                | Indicates the performance specifications. Its value can be any of the following:                        |
      |                       |                       |                                                                                                         |
      |                       |                       | -  **normal**: general-enhanced                                                                         |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "flavors": [{
                  "vcpus": "1",
                  "ram": 2,
                              "id":"2988b9cc-2aac-3a94-898c-14666702f129",
                  "spec_code": "rds.mysql.c2.medium.ha",
                              "version_name": ["5.6","5.7","8.0"],
                  "instance_mode": "ha",
                  "az_status": {
                      "az1": "normal",
                      "az2": "normal"
                  },
                  "az_desc": {
                      "az1": "az1",
                      "az2": "az2"
                  },
                              "group_type": "normal"
              },
              {
                  "vcpus": "1",
                  "ram": 2,
                              "id":"2988b9cc-2aac-3a94-898c-14666702f130",
                  "spec_code": "rds.mysql.c2.medium.rr",
                              "version_name": ["5.6","5.7","8.0"],
                  "instance_mode": "replica",
                  "az_status": {
                      "az1": "normal",
                      "az2": "normal"
                  },
                  "az_desc": {
                      "az1": "az1",
                      "az2": "az2"
                  },
                              "group_type": "normal"
              }
          ]
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
