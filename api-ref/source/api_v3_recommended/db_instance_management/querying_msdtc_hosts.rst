:original_name: rds_08_0036.html

.. _rds_08_0036:

Querying MSDTC Hosts
====================

Function
--------

This API is used to query MSDTC hosts.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is available only for RDS for SQL Server.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/msdtc/hosts?offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** URI Parameters

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                      |
      +=================+=================+=================+==================================================================================================+
      | project_id      | Yes             | String          | Specifies the project ID of a tenant in a region.                                                |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | instance_id     | Yes             | String          | Specifies the DB instance ID.                                                                    |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Index offset. The query starts from the next piece of data indexed by this parameter.            |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The value must be a non-negative number.                                                         |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The default value is **0**, indicating that the query starts from the first data record.         |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Number of records to be queried.                                                                 |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The value ranges from 1 to 100.                                                                  |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The default value is **10**.                                                                     |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

Request example
---------------

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

   GET https://rds.eu-de.otc.t-systems.com/v3/054b93101a00d3a02fe3c01fb31462ac/instances/8ef19e30cbf44c79b63c7e6b2168a400in04/msdtc/hosts

Response
--------

-  Normal response

   .. table:: **Table 3** Response body parameters

      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                       |
      +=======================+=======================+===================================================================+
      | total_count           | Integer               | Total number of hosts.                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | hosts                 | Array of objects      | Host list.                                                        |
      |                       |                       |                                                                   |
      |                       |                       | For details, see :ref:`Table 4 <rds_08_0036__table944417166471>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------+

   .. _rds_08_0036__table944417166471:

   .. table:: **Table 4** Hosts element structure description

      ========= ====== =============
      Parameter Type   Description
      ========= ====== =============
      id        String Host ID.
      host      String Host address.
      host_name String Host name.
      ========= ====== =============

-  Example normal response

   .. code-block::

      {
         "total_count" : 1,
         "hosts" : [ {
           "id" : "527dd9ca-cc2c-4bac-8707-f9b4f55343f4",
           "host" : "192.168.0.90",
           "host_name" : "MSSQL-00E5FB7A"
         } ]
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
