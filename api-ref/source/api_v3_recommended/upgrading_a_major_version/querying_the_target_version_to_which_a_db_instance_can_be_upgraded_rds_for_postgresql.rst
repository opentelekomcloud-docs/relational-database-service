:original_name: rds_19_0001.html

.. _rds_19_0001:

Querying the Target Version to Which a DB Instance Can Be Upgraded (RDS for PostgreSQL)
=======================================================================================

Function
--------

This API is used to query the target version to which an RDS for PostgreSQL DB instance can be upgraded.

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

-  Before a major version upgrade, perform an upgrade check. If there is no successful upgrade check in the validity period, a major version upgrade is not allowed.

URI
---

-  URI format

   GET /v3/{project_id}/instances/{instance_id}/major-version/available-version

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

   None

-  Example

   .. code-block::

      https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/3aa441c4c98a4b36b100a7e3e87d17cein03/major-version/available-version

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      ================== ================ ===================
      Name               Type             Description
      ================== ================ ===================
      available_versions Array of Strings Available versions.
      ================== ================ ===================

-  Example normal response

   .. code-block::

      {
               "available_versions": ["13.9", "14.4"]
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
