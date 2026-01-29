:original_name: rds_21_0005.html

.. _rds_21_0005:

Disabling Database Proxy
========================

Function
--------

This API is used to disable database proxy of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   DELETE https://{Endpoint}/v3/{project_id}/instances/{instance_id}/proxy/{proxy_id}

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | proxy_id              | Yes                   | Database proxy ID.                                                                               |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

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

      DELETE https://rds.eu-de.otc.t-systems.com/v3/23a50154cf494ec9ad6883979a12db0a/instances/ba0fd7c13cca4655820e0f858d5d467bin01/proxy/4e2a0c70f70f4807940db73a30b5b522po01

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      ========= ====== ===========
      Parameter Type   Description
      ========= ====== ===========
      job_id    String Task ID.
      ========= ====== ===========

-  Example normal response

   .. code-block::

      {
         "job_id" : "09908118-8e32-4742-982a-7be194f59e1d"
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
