:original_name: rds_17_0002.html

.. _rds_17_0002:

Obtaining the Result of a Specific Diagnosis Item
=================================================

Function
--------

This API is used to obtain the result of a specific diagnosis item.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*endpoint*}/v3/{project_id}/instances/diagnosis/info

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Request parameters

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                      |
      +=================+=================+=================+==================================================================================================================================================================================================================================================+
      | engine          | Yes             | String          | Engine type.                                                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                  |
      |                 |                 |                 | Enumerated values:                                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                  |
      |                 |                 |                 | -  mysql                                                                                                                                                                                                                                         |
      |                 |                 |                 | -  postgresql                                                                                                                                                                                                                                    |
      |                 |                 |                 | -  sqlserver                                                                                                                                                                                                                                     |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | diagnosis       | Yes             | String          | Diagnosis item.                                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                  |
      |                 |                 |                 | Enumerated values:                                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                  |
      |                 |                 |                 | -  high_pressure                                                                                                                                                                                                                                 |
      |                 |                 |                 | -  lock_wait                                                                                                                                                                                                                                     |
      |                 |                 |                 | -  insufficient_capacity                                                                                                                                                                                                                         |
      |                 |                 |                 | -  slow_sql_frequency                                                                                                                                                                                                                            |
      |                 |                 |                 | -  disk_performance_cap                                                                                                                                                                                                                          |
      |                 |                 |                 | -  mem_overrun                                                                                                                                                                                                                                   |
      |                 |                 |                 | -  age_exceed                                                                                                                                                                                                                                    |
      |                 |                 |                 | -  connections_exceed                                                                                                                                                                                                                            |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Index offset.                                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                  |
      |                 |                 |                 | If **offset** is set to *N*, the resource query starts from the *N*\ +1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value must be a number but cannot be a negative number. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Number of returned results. Default value: **10**                                                                                                                                                                                                |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   .. table:: **Table 3** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  URI example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/diagnosis/info?engine=sqlserver&diagnosis=high_pressure&offset=1&limit=10

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                     |
      +=======================+=======================+=================================================================================================+
      | diagnosis             | String                | Diagnosis item.                                                                                 |
      |                       |                       |                                                                                                 |
      |                       |                       | Enumerated values:                                                                              |
      |                       |                       |                                                                                                 |
      |                       |                       | -  high_pressure                                                                                |
      |                       |                       | -  lock_wait                                                                                    |
      |                       |                       | -  insufficient_capacity                                                                        |
      |                       |                       | -  slow_sql_frequency                                                                           |
      |                       |                       | -  disk_performance_cap                                                                         |
      |                       |                       | -  mem_overrun                                                                                  |
      |                       |                       | -  age_exceed                                                                                   |
      |                       |                       | -  connections_exceed                                                                           |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | total_count           | Integer               | Number of instances.                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | instances             | Array of objects      | Specifies the DB instance ID.                                                                   |
      |                       |                       |                                                                                                 |
      |                       |                       | For details, see :ref:`Table 5 <rds_17_0002__en-us_topic_0000001745910893_table1950773843311>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+

   .. _rds_17_0002__en-us_topic_0000001745910893_table1950773843311:

   .. table:: **Table 5** instances field data structure description

      ==== ====== =============================
      Name Type   Description
      ==== ====== =============================
      id   String Specifies the DB instance ID.
      ==== ====== =============================

-  Example normal response

   .. code-block::

      {
        "diagnosis" : "high_pressure",
        "total_count" : 1,
        "instances" : [ {
          "id" : "abd21a25fdedfd6db69721f4b761bc38in04"
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
