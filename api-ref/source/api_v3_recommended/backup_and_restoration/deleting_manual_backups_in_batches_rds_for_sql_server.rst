:original_name: rds_09_0018.html

.. _rds_09_0018:

Deleting Manual Backups in Batches (RDS for SQL Server)
=======================================================

Function
--------

This API is used to delete manual backups in batches.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is only available for RDS for SQL Server instances.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/backups/batch-delete

-  Parameter description

   .. table:: **Table 1** URI Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
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

   +-----------------+-----------------+------------------+------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                              |
   +=================+=================+==================+==========================================+
   | backup_ids      | Yes             | Array of strings | IDs of the manual backups to be deleted. |
   |                 |                 |                  |                                          |
   |                 |                 |                  | Value range: [1, 50]                     |
   +-----------------+-----------------+------------------+------------------------------------------+

Example Request
---------------

Delete manual backups in batches.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/backups/batch-delete

   {
     "backup_ids" : [ "53ad33abe43976054br04", "63ad3439af9776054br04" ]
   }

Response
--------

-  Response parameters

   .. table:: **Table 4** Response body parameters

      +----------------+------------------+--------------------------------------------------------------------------------------------------------------------------+
      | Name           | Type             | Description                                                                                                              |
      +================+==================+==========================================================================================================================+
      | delete_results | Array of objects | Backup deletion results. For details, see :ref:`Table 5 <rds_09_0018__en-us_topic_0000002263777974_table1274521515288>`. |
      +----------------+------------------+--------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0018__en-us_topic_0000002263777974_table1274521515288:

   .. table:: **Table 5** delete_results field data structure description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                      |
      +=======================+=======================+==================================================================================+
      | backup_id             | String                | Backup ID.                                                                       |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------+
      | error_code            | String                | Code returned after a task is submitted.                                         |
      |                       |                       |                                                                                  |
      |                       |                       | -  If the task is executed successfully, **0** is returned.                      |
      |                       |                       | -  If the task fails to be executed, the specific error code is returned.        |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------+
      | error_msg             | String                | Description returned after a task is submitted.                                  |
      |                       |                       |                                                                                  |
      |                       |                       | -  If the task is executed successfully, **Success** is returned.                |
      |                       |                       | -  If the task fails to be executed, the specific error information is returned. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "delete_results" : [ {
          "backup_id" : "dsfae23fsfdsae3435br04",
          "error_code" : "DBS.200054",
          "error_msg" : "the backup is in use"
        } ,
      {
          "backup_id" : "ed23545223fsfdsae3435br04",
          "error_code" : "0",
          "error_msg" : "Success"
        }
      ] }

Status Code
-----------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
