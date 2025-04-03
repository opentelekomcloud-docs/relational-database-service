:original_name: rds_19_0003.html

.. _rds_19_0003:

Querying the Major Version Check Status or Upgrade Status of a DB Instance (RDS for PostgreSQL)
===============================================================================================

Function
--------

This API is used to query the major version check status or upgrade status.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is available to RDS for PostgreSQL only.
-  Major version upgrades are available to the following versions:

   -  RDS for PostgreSQL 12: 12.7 or later
   -  RDS for PostgreSQL 13: 13.3 or later
   -  RDS for PostgreSQL 14: 14.4 or later

-  Due to OS restrictions, some instances do not support major version upgrades. To learn which versions your instance can be upgraded to, see the list of available versions on the :ref:`Querying the Target Version to Which a DB Instance Can Be Upgraded (RDS for PostgreSQL) <rds_19_0001>`.
-  Before a major version upgrade, perform an upgrade check. If there is no successful upgrade check in the validity period, a major version upgrade is not allowed.

URI
---

-  URI format

   GET /v3/{project_id}/instances/{instance_id}/major-version/status?action={current_action}

-  Parameters

   .. table:: **Table 1** Parameters

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
      | Parameter       | Type            | Mandatory       | Description                                                         |
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

      +-----------------+-----------------+-----------------+---------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                             |
      +=================+=================+=================+=========================================================+
      | action          | String          | Yes             | The status to be queried.                               |
      |                 |                 |                 |                                                         |
      |                 |                 |                 | -  **check**: Check the pre-upgrade check status.       |
      |                 |                 |                 | -  **upgrade**: Check the major version upgrade status. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------+

-  URI example

   .. code-block::

      https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/3aa441c4c98a4b36b100a7e3e87d17cein03/major-version/status?action=upgrade

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                                                           |
      +=======================+=======================+=======================================================================================================================================================================================================+
      | status                | String                | Major version upgrade status or Pre-check status of the instance.                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                       |
      |                       |                       | -  **running**: The pre-check or major version upgrade is in progress.                                                                                                                                |
      |                       |                       | -  **success**: The pre-check or major version upgrade is successful.                                                                                                                                 |
      |                       |                       | -  **failed**: The pre-check or major version upgrade fails.                                                                                                                                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | target_version        | String                | Target version.                                                                                                                                                                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time            | String                | Start time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | check_expiration_time | String                | Time when a check report expires. The format is yyyy-mm-ddThh:mm:ssZ.                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | detail                | String                | Details about the pre-check or upgrade report.                                                                                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
           "status": "success",
           "target_version": "14.4.1",
           "start_time": "2023-03-06T02:33:49+0800",
           "check_expiration_time": "2023-03-13T02:33:49+0800",
           "detail": "2023-03-06 18:33:26 --- pg_upgrade check task                                       begin\n2023-03-06 18:34:40 --- pg_upgrade check on master:                            [user_check_report]User check success "
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
