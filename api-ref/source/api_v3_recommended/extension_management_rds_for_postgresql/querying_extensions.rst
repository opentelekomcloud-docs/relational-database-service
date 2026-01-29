:original_name: rds_11_0010.html

.. _rds_11_0010:

Querying Extensions
===================

Function
--------

This API is used to obtain extension information of a specified database.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This operation cannot be performed when the DB instance is in any of the following statuses: creating, changing instance class, changing port, or abnormal.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/extensions?database_name={database_name}&offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                            |
      +=======================+=======================+========================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                      |
      |                       |                       |                                                                                                                                        |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                       |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                                                          |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | database_name         | Yes                   | The name of the specific database created inside the RDS instance. This is the logical database name, not the RDS instance identifier. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Index offset. The query starts from the next piece of data indexed by this parameter.                                                  |
      |                       |                       |                                                                                                                                        |
      |                       |                       | The value must be a non-negative number.                                                                                               |
      |                       |                       |                                                                                                                                        |
      |                       |                       | The default value is **0**, indicating that the query starts from the first data record.                                               |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Number of records to be queried.                                                                                                       |
      |                       |                       |                                                                                                                                        |
      |                       |                       | The value ranges from 1 (inclusive) to 100 (inclusive).                                                                                |
      |                       |                       |                                                                                                                                        |
      |                       |                       | The default value is **100**.                                                                                                          |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  URI example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/f569f1358436479dbcba8603c32cc4aein03/extensions?database_name=db1

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      +-------------+------------------+------------------------------------------------------------------------------------+
      | Parameter   | Type             | Description                                                                        |
      +=============+==================+====================================================================================+
      | extensions  | Array of objects | Extension list. For details, see :ref:`Table 4 <rds_11_0010__table1457984914368>`. |
      +-------------+------------------+------------------------------------------------------------------------------------+
      | total_count | Integer          | Total number of extensions.                                                        |
      +-------------+------------------+------------------------------------------------------------------------------------+

   .. _rds_11_0010__table1457984914368:

   .. table:: **Table 4** extensions element structure description

      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                | Type    | Description                                                                                                                                             |
      +==========================+=========+=========================================================================================================================================================+
      | name                     | String  | Extension name.                                                                                                                                         |
      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | database_name            | String  | The name of the specific database created inside the RDS instance. This is the logical database name, not the RDS instance identifier.                  |
      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | version                  | String  | Extension version.                                                                                                                                      |
      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | version_update           | String  | New version that the extension can be upgraded to. If the value of this parameter is different from that of **version**, the extension can be upgraded. |
      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | shared_preload_libraries | String  | Dependent preloaded library.                                                                                                                            |
      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created                  | Boolean | Whether the extension has been created.                                                                                                                 |
      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description              | String  | Extension description.                                                                                                                                  |
      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enable_install           | Boolean | Whether the extension can be installed.                                                                                                                 |
      +--------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
         "extensions" : [ {
           "name" : "pg_cron",
           "database_name" : "db1",
           "version" : "1.0",
           "version_update" : "1.0",
           "shared_preload_libraries" : "pg_cron",
           "created" : false,
           "enable_install": false,
           "description" : "pg_cron access method - signature file based index"
       } ],
         "total_count" : 1
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
