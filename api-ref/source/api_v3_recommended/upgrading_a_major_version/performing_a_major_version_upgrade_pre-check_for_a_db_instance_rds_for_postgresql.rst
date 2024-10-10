:original_name: rds_19_0002.html

.. _rds_19_0002:

Performing a Major Version Upgrade Pre-Check for a DB Instance (RDS for PostgreSQL)
===================================================================================

Function
--------

This API is used to perform a health check before a major version upgrade.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is available to RDS for PostgreSQL only.
-  This operation cannot be performed when the DB instance is in any of the following statuses: creating, changing instance specifications, changing port, frozen, or abnormal.
-  Major version upgrades are available to the following versions:

   -  RDS for PostgreSQL 12: 12.7 or later
   -  RDS for PostgreSQL 13: 13.3 or later
   -  RDS for PostgreSQL 14: 14.4 or later
   -  Major version upgrades are unavailable to RDS for PostgreSQL 11.

-  Due to OS restrictions, some instances do not support major version upgrades. To learn which versions your instance can be upgraded to, see the list of available versions on the :ref:`Querying the Target Version to Which a DB Instance Can Be Upgraded (RDS for PostgreSQL) <rds_19_0001>`.
-  Before a major version upgrade, perform an upgrade check. If there is no successful upgrade check in the validity period, a major version upgrade is not allowed.

URI
---

-  URI format

   POST /v3/{project_id}/instances/{instance_id}/major-version/inspection

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                         |
      +=================+=================+=================+=====================================================================+
      | project_id      | String          | Yes             | Project ID of a tenant in a region.                                 |
      |                 |                 |                 |                                                                     |
      |                 |                 |                 | To obtain it, refer to :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
      | instance_id     | String          | Yes             | Instance ID.                                                        |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

Request
-------

-  Request parameters

   .. table:: **Table 2** Parameter description

      ============== ====== ========= ===========================
      Name           Type   Mandatory Description
      ============== ====== ========= ===========================
      target_version String Yes       Target version of database.
      ============== ====== ========= ===========================

-  URI example

   .. code-block::

      https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/3aa441c4c98a4b36b100a7e3e87d17cein03/major-version/inspection
      {
          "target_version": "14.9.0"
      }

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      ========= ====== ================
      Name      Type   Description
      ========= ====== ================
      report_id String Check report ID.
      ========= ====== ================

-  Example normal response

   .. code-block::

      {
               "report_id": "f7a8e35e-a14c-4e5e-b1f0-d3764e8ed8a8"
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
