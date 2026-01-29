:original_name: rds_21_0003.html

.. _rds_21_0003:

Querying Database Proxy Specifications
======================================

Function
--------

This API is used to query database proxy specifications of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This operation cannot be performed when the instance is in the abnormal or frozen state.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/proxy/flavors?offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                      |
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
      |                 |                 |                 | The value ranges from 1 (inclusive) to 100 (inclusive).                                          |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The default value is **100**.                                                                    |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

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

   .. code-block:: text

      GET https://rds.eu-de.otc.t-systems.com/v3/23a50154cf494ec9ad6883979a12db0a/instances/ba0fd7c13cca4655820e0f858d5d467bin01/proxy/flavors?offset=0&limit=100

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                     |
      +=======================+=======================+=================================================================================================+
      | compute_flavor_groups | Array of objects      | Specification group information.                                                                |
      |                       |                       |                                                                                                 |
      |                       |                       | For details, see :ref:`Table 4 <rds_21_0003__en-us_topic_0000001836635801_table1457984914368>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+

   .. _rds_21_0003__en-us_topic_0000001836635801_table1457984914368:

   .. table:: **Table 4** compute_flavor_groups element structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | group_type            | String                | Specification group type.                                                                        |
      |                       |                       |                                                                                                  |
      |                       |                       | -  X86                                                                                           |
      |                       |                       | -  ARM                                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | compute_flavors       | Array of objects      | Specification information.                                                                       |
      |                       |                       |                                                                                                  |
      |                       |                       | For details, see :ref:`Table 5 <rds_21_0003__en-us_topic_0000001836635801_table52411536133812>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

   .. _rds_21_0003__en-us_topic_0000001836635801_table52411536133812:

   .. table:: **Table 5** compute_flavors element structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================================================================================================+
      | id                    | String                | Specification ID of the database proxy.                                                                                                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | code                  | String                | Specification code of the database proxy.                                                                                                                                                                                           |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | cpu                   | String                | Number of vCPUs.                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                     |
      |                       |                       | For example, the value **1** indicates one vCPU.                                                                                                                                                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mem                   | String                | Memory size in GB.                                                                                                                                                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | db_type               | String                | Only specifications whose database type is database proxy are returned. The return value is Proxy.                                                                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | az_status             | Object                | AZ information. **key** indicates the AZ associated with the specification, and **value** indicates the specification status in the AZ. Only the specification status in the AZ where the primary instance is located is displayed. |
      |                       |                       |                                                                                                                                                                                                                                     |
      |                       |                       | -  **normal**: The specification is normal.                                                                                                                                                                                         |
      |                       |                       | -  **abandon**: The specification is abandoned.                                                                                                                                                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
         "compute_flavor_groups" : [ {
           "group_type" : "X86",
           "compute_flavors" : [ {
             "id" : "3208f282-7815-4ff8-9466-90a6fedd6b52",
             "code" : "rds.proxy.large.2",
             "cpu" : "2",
             "mem" : "4",
             "db_type" : "Proxy",
             "az_status" : {
               "aaa" : "normal"
             }
           } ]
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
