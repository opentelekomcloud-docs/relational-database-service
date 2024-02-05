:original_name: rds_05_0024.html

.. _rds_05_0024:

Upgrading a Minor Version
=========================

Function
--------

This API is used to upgrade minor versions of RDS for MySQL or RDS for PostgreSQL instances.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is supported for MySQL and PostgreSQL DB engines.

The constraints on minor version upgrades for RDS for PostgreSQL are as follows:

-  The minor version cannot be upgraded for instances with abnormal nodes.

-  The following minor versions cannot be upgraded:

   - Versions earlier than 11.2 for RDS for PostgreSQL 11

   - The upgrade will be performed immediately upon the submission of your request. Delayed upgrade of minor versions is not supported.

URI
---

-  URI format

   POST /v3/{project_id}/instances/{instance_id}/action/db-upgrade

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

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================+
      | delay           | No              | Boolean         | Whether to delay the upgrade until the maintenance window.                                                                                            |
      |                 |                 |                 |                                                                                                                                                       |
      |                 |                 |                 | -  **true**: Delay the upgrade. This value is only available to RDS for MySQL. The instance will be upgraded during the specified maintenance window. |
      |                 |                 |                 | -  **false**: Upgrade the instance immediately (default value).                                                                                       |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   POST https://rds.eu-de.otc.t-systems.com/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/5b409baece064984a1b3eef6addae50cin01/action/db-upgrade

-  Request example

   .. code-block:: text

      {
          "delay":false
      }

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      ====== ====== ===========
      Name   Type   Description
      ====== ====== ===========
      job_id String Job ID.
      ====== ====== ===========

-  Example normal response

   .. code-block:: text

      {
          "job_id": "2b414788a6004883a02390e2eb0ea227"
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
