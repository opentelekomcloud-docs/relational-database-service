:original_name: rds_17_0001.html

.. _rds_17_0001:

Obtaining the Number of Instances After Diagnosis
=================================================

Function
--------

This API is used to obtain the number of instances after diagnosis.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*endpoint*}/v3/{project_id}/instances/diagnosis

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

      +-----------------+-----------------+-----------------+--------------------+
      | Parameter       | Mandatory       | Type            | Description        |
      +=================+=================+=================+====================+
      | engine          | Yes             | String          | Engine type.       |
      |                 |                 |                 |                    |
      |                 |                 |                 | Enumerated values: |
      |                 |                 |                 |                    |
      |                 |                 |                 | -  mysql           |
      |                 |                 |                 | -  postgresql      |
      |                 |                 |                 | -  sqlserver       |
      +-----------------+-----------------+-----------------+--------------------+

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

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/diagnosis?engine=sqlserver

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                     |
      +=======================+=======================+=================================================================================================+
      | diagnosis             | Array of objects      | Diagnosis details.                                                                              |
      |                       |                       |                                                                                                 |
      |                       |                       | For details, see :ref:`Table 5 <rds_17_0001__en-us_topic_0000001745831081_table1950773843311>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+

   .. _rds_17_0001__en-us_topic_0000001745831081_table1950773843311:

   .. table:: **Table 5** diagnosis field data structure description

      ===== ======= ====================
      Name  Type    Description
      ===== ======= ====================
      name  String  Diagnosis item.
      count Integer Number of instances.
      ===== ======= ====================

-  Example normal response

   .. code-block::

      {
         "diagnosis" : [ {
           "name" : "high_pressure",
           "count" : 1
         }, {
           "name" : "lock_wait",
           "count" : 2
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
