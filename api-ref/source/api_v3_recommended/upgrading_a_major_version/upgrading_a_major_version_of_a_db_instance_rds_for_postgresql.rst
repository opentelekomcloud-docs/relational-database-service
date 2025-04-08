:original_name: rds_19_0005.html

.. _rds_19_0005:

Upgrading a Major Version of a DB Instance (RDS for PostgreSQL)
===============================================================

Function
--------

This API is used to upgrade a major version.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is available to RDS for PostgreSQL only.
-  This operation cannot be performed when the DB instance is in any of the following statuses: creating, changing instance specifications, changing port, frozen, or abnormal.
-  Before an upgrade, ensure that a valid upgrade check report is available. In the check report, the source version is the current instance version, the target version is the one contained in the request body, the check is performed within seven days, and the check result is successful.
-  Major version upgrades are available to the following versions:

   -  RDS for PostgreSQL 12: 12.7 or later
   -  RDS for PostgreSQL 13: 13.3 or later
   -  RDS for PostgreSQL 14: 14.4 or later

-  Due to OS restrictions, some instances do not support major version upgrades. To learn which versions your instance can be upgraded to, see the list of available versions on the :ref:`Querying the Target Version to Which a DB Instance Can Be Upgraded (RDS for PostgreSQL) <rds_19_0001>`.
-  Before a major version upgrade, perform an upgrade check. If there is no successful upgrade check in the validity period, a major version upgrade is not allowed.

URI
---

-  URI format

   POST /v3/{project_id}/instances/{instance_id}/major-version/upgrade

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

   +----------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                       | Type            | Mandatory       | Description                                                                                                                                                |
   +============================+=================+=================+============================================================================================================================================================+
   | target_version             | String          | Yes             | Target version.                                                                                                                                            |
   |                            |                 |                 |                                                                                                                                                            |
   |                            |                 |                 | It must be later than the current major version of the instance. For example, if the current major version is 12, the target version must be 13 or 14.     |
   +----------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_change_private_ip       | Boolean         | Yes             | Whether to switch the floating IP address of the source instance to the target instance.                                                                   |
   |                            |                 |                 |                                                                                                                                                            |
   |                            |                 |                 | -  **true**: After the upgrade, the floating IP address is switched to the target instance.                                                                |
   |                            |                 |                 | -  **false**: After the upgrade, the floating IP address of the source instance remains unchanged, and the target instance uses a new floating IP address. |
   +----------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | statistics_collection_mode | String          | No              | Mode of collecting statistics. It is mandatory if **is_change_private_ip** is set to **true**.                                                             |
   |                            |                 |                 |                                                                                                                                                            |
   |                            |                 |                 | -  **before_change_private_ip**: Statistics are collected before the floating IP address of the source instance is switched to the target instance.        |
   |                            |                 |                 | -  **after_change_private_ip**: Statistics are collected after the floating IP address of the source instance is switched to the target instance.          |
   +----------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/3aa441c4c98a4b36b100a7e3e87d17cein03/major-version/upgrade
      {
         "target_version":  "14.6.1",
         "is_change_private_ip":  true,
         "statistics_collection_mode":  "before_change_private_ip"
      }

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      ====== ====== ===========
      Name   Type   Description
      ====== ====== ===========
      job_id String Task ID.
      ====== ====== ===========

-  Example normal response

   .. code-block::

      {
         "job_id": "3afe25b7-4523-4d3b-8236-7121be922691"
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
