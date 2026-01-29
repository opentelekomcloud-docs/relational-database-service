:original_name: rds_08_0035.html

.. _rds_08_0035:

Adding Host Addresses for MSDTC
===============================

Function
--------

This API is used to add host addresses for Microsoft Distributed Transaction Coordinator (MSDTC).

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is available only for RDS for SQL Server.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/msdtc/host

-  Parameter description

   .. table:: **Table 1** URI Parameters

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

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | Content-Type    | Yes             | String          | The content type.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The default value is **application/json**.                                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type             | Description                                                                                                                            |
   +=================+=================+==================+========================================================================================================================================+
   | hosts           | Yes             | Array of objects | Host information.                                                                                                                      |
   |                 |                 |                  |                                                                                                                                        |
   |                 |                 |                  | For details on the element structure, see :ref:`Table 4 <rds_08_0035__en-us_topic_0271461297_en-us_topic_0145282472_table1531087569>`. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------+

.. _rds_08_0035__en-us_topic_0271461297_en-us_topic_0145282472_table1531087569:

.. table:: **Table 4** Hosts data structure description

   ========= ========= ====== ================
   Name      Mandatory Type   Description
   ========= ========= ====== ================
   host_name Yes       String Host name.
   ip        Yes       String Host IP address.
   ========= ========= ====== ================

Request example
---------------

Add host addresses for MSDTC.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/054b93101a00d3a02fe3c01fb31462ac/instances/463a6520abc345888850ea5bfb245e4fin04/msdtc/host

   {
      "hosts" : [ {
        "host_name" : "pc1",
        "ip" : "127.0.0.1"
      } ]
    }

Response
--------

-  Normal response

   .. table:: **Table 5** Response body parameters

      ====== ====== ===========
      Name   Type   Description
      ====== ====== ===========
      job_id String Task ID.
      ====== ====== ===========

-  Example normal response

   .. code-block::

      {
         "job_id" : "603d87db-9a91-411e-b369-ca4d72007e27"
       }

-  Abnormal response

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
