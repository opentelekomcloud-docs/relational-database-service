:original_name: rds_11_0013.html

.. _rds_11_0013:

Modifying the Value of a Specified Parameter for an Instance
============================================================

Function
--------

This API is used to modify the value of a specified parameter for an instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This operation cannot be performed when the DB instance is in the abnormal state.
-  Parameters of read replicas cannot be modified.
-  Only the value of **shared_preload_libraries** can be modified.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/parameter/{name}

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
      | name                  | Yes                   | Parameter name.                                                                                  |
      |                       |                       |                                                                                                  |
      |                       |                       | Only the **shared_preload_libraries** parameter can be modified.                                 |
      |                       |                       |                                                                                                  |
      |                       |                       | The default value is **shared_preload_libraries**.                                               |
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

.. table:: **Table 3** Parameters

   ========= ========= ====== ================
   Parameter Mandatory Type   Description
   ========= ========= ====== ================
   value     Yes       String Parameter value.
   ========= ========= ====== ================

Example Request
---------------

Change the value of **shared_preload_libraries** for a DB instance.

.. code-block:: text

   PUT https://rds.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/f569f1358436479dbcba8603c32cc4aein03/parameter/shared_preload_libraries
   {
     "value" : "passwordcheck.so,pg_stat_statements,pg_sql_history"
   }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameters

      +-----------------------+-----------------------+--------------------------------------------------------+
      | Parameter             | Type                  | Description                                            |
      +=======================+=======================+========================================================+
      | job_id                | String                | Task ID.                                               |
      +-----------------------+-----------------------+--------------------------------------------------------+
      | restart_required      | Boolean               | Whether a reboot is required. The value can be:        |
      |                       |                       |                                                        |
      |                       |                       | -  **true**: indicates that a reboot is required.      |
      |                       |                       | -  **false**: indicates that a reboot is not required. |
      +-----------------------+-----------------------+--------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
        "job_id" : "e7a7535b-eb9b-45ac-a83a-020dc5016d94",
        "restart_required" : true
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
