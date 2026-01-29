:original_name: rds_05_0024.html

.. _rds_05_0024:

Upgrading the Minor Version of a DB Instance
============================================

Function
--------

This API is used to upgrade minor versions of RDS for MySQL or RDS for PostgreSQL instances.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is available to RDS for MySQL and RDS for PostgreSQL only.
-  The minor versions of any RDS for PostgreSQL instances containing abnormal nodes cannot be upgraded.
-  For RDS for PostgreSQL, minor versions can be upgraded immediately upon request submission only, but not during the specified maintenance window.
-  A minor version upgrade of RDS for PostgreSQL instances can cause a primary/standby switchover.

URI
---

-  URI format

   POST /v3/{project_id}/instances/{instance_id}/db-upgrade

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                                              |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Instance ID.                                                                                     |
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

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                      |
   +=================+=================+=================+==================================================================================================================+
   | is_delayed      | No              | Boolean         | Whether to delay the upgrade until the maintenance window. Valid values:                                         |
   |                 |                 |                 |                                                                                                                  |
   |                 |                 |                 | -  **true**: The upgrade will be delayed. The instance will be upgraded during the specified maintenance window. |
   |                 |                 |                 | -  **false** (default): The instance is upgraded immediately.                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Upgrade the minor version of a DB instance.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/5b409baece064984a1b3eef6addae50cin01/db-upgrade

   {
      "is_delayed" : false
    }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      ====== ====== ===========
      Name   Type   Description
      ====== ====== ===========
      job_id String Task ID.
      ====== ====== ===========

-  Example normal response

   .. code-block::

      {
        "job_id" : "e7a7535b-eb9b-45ac-a83a-020dc5016d94"
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
