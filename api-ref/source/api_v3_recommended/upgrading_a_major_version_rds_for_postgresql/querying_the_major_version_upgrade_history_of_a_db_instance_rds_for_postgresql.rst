:original_name: rds_19_0006.html

.. _rds_19_0006:

Querying the Major Version Upgrade History of a DB Instance (RDS for PostgreSQL)
================================================================================

Function
--------

This API is used to query the major version upgrade history.

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

-  Due to OS restrictions, some instances do not support major version upgrades. To learn which versions your instance can be upgraded to, see the list of available versions on the :ref:`Querying the Target Version to Which a DB Instance Can Be Upgraded (RDS for PostgreSQL) <rds_19_0001>`.
-  Before a major version upgrade, perform an upgrade check. If there is no successful upgrade check in the validity period, a major version upgrade is not allowed.

URI
---

-  URI format

   GET /v3/{project_id}/instances/{instance_id}/major-version/upgrade-histories?offset={offset}&limit={limit}&order={order}&sort_field={sort_field}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                                                                                                                                                                                                    |
      +=================+=================+=================+================================================================================================================================================================================================================================================================+
      | project_id      | String          | Yes             | Project ID of a tenant in a region.                                                                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                                |
      |                 |                 |                 | To obtain it, refer to :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                                                                                                                                            |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id     | String          | Yes             | Instance ID.                                                                                                                                                                                                                                                   |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | Integer         | No              | Index offset. If **offset** is set to *N*, the resource query starts from the *N*\ +1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value must be a number but cannot be a negative number. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | Integer         | No              | Number of query records. The default value is **10**. The value must be a positive integer. The minimum value is **1** and the maximum value is **100**.                                                                                                       |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | order           | String          | No              | Sorting order.                                                                                                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                                                |
      |                 |                 |                 | -  **DESC**: descending order                                                                                                                                                                                                                                  |
      |                 |                 |                 | -  **ASC**: ascending order                                                                                                                                                                                                                                    |
      |                 |                 |                 | -  Default value: **desc**                                                                                                                                                                                                                                     |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | sort_field      | String          | No              | Sorting field.                                                                                                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                                                |
      |                 |                 |                 | -  **start_time**: specifies the start time.                                                                                                                                                                                                                   |
      |                 |                 |                 | -  **end_time**: specifies the end time.                                                                                                                                                                                                                       |
      |                 |                 |                 | -  Default value: **start_time**                                                                                                                                                                                                                               |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  URI example

   .. code-block::

      https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/3aa441c4c98a4b36b100a7e3e87d17cein03/major-version/upgrade-histories?offset=0&limit=10

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                    |
      +=======================+=======================+================================================================================================+
      | total_count           | Integer               | Total number of records.                                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
      | upgrade_reports       | Array of objects      | Upgrade report details.                                                                        |
      |                       |                       |                                                                                                |
      |                       |                       | For details, see :ref:`Table 3 <rds_19_0006__en-us_topic_0000001718121990_table972752710237>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+

   .. _rds_19_0006__en-us_topic_0000001718121990_table972752710237:

   .. table:: **Table 3** upgrade_report field data structure description

      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                       | Type                  | Description                                                                                                                                                                                           |
      +============================+=======================+=======================================================================================================================================================================================================+
      | id                         | String                | Upgrade report ID.                                                                                                                                                                                    |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time                 | String                | Upgrade start time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                              |
      |                            |                       |                                                                                                                                                                                                       |
      |                            |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time                   | String                | Upgrade end time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                |
      |                            |                       |                                                                                                                                                                                                       |
      |                            |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | src_instance_id            | String                | Source instance ID.                                                                                                                                                                                   |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | src_database_version       | String                | Source instance version.                                                                                                                                                                              |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | dst_instance_id            | String                | Target instance ID.                                                                                                                                                                                   |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | dst_database_version       | String                | Target instance version.                                                                                                                                                                              |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | result                     | String                | Upgrade result.                                                                                                                                                                                       |
      |                            |                       |                                                                                                                                                                                                       |
      |                            |                       | -  **success**: The upgrade is successful.                                                                                                                                                            |
      |                            |                       | -  **failed**: The upgrade fails.                                                                                                                                                                     |
      |                            |                       | -  **running**: The upgrade is in progress.                                                                                                                                                           |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | is_private_ip_changed      | Boolean               | Whether to switch the floating IP address of the source instance to the target instance.                                                                                                              |
      |                            |                       |                                                                                                                                                                                                       |
      |                            |                       | -  **true**: indicates that the floating IP address of the source instance will be switched to the target instance.                                                                                   |
      |                            |                       | -  **false**: indicates that the floating IP address of the source instance will not be switched to the target instance.                                                                              |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | private_ip_change_time     | String                | Time when the floating IP address is changed. The format is yyyy-mm-ddThh:mm:ssZ.                                                                                                                     |
      |                            |                       |                                                                                                                                                                                                       |
      |                            |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | statistics_collection_mode | String                | When to collect statistics.                                                                                                                                                                           |
      |                            |                       |                                                                                                                                                                                                       |
      |                            |                       | -  **before_change_private_ip**: Statistics are collected before the floating IP address is changed.                                                                                                  |
      |                            |                       | -  **after_change_private_ip**: Statistics are collected after the floating IP address is changed.                                                                                                    |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | detail                     | String                | Upgrade report details.                                                                                                                                                                               |
      +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
               "total_count": 1,
               "upgrade_reports": [
                        {
                                  "id": "1a8fda5a-17a6-ebc4-bf1f-97ae837f432b",
                                  "start_time": "2023-03-06T02:45:49+0800",
                                  "end_time": "2023-03-06T02:50:49+0800",
                                  "src_instance_id": "dccacebb7b884ee18bc5c02c918ef2b0in03",
                                  "src_database_version": "13.9",
                                  "dst_instance_id": "6b5750504be1403191c4f00e4ffaee5ein03",
                                  "dst_database_version": "14.6",
                                  "result": "success",
                                  "is_private_ip_changed": true,
                                  "private_ip_change_time": "2023-03-06T03:10:49+0800",
                                  "statistics_collection_mode": "before_change_private_ip",
                                  "detail": "2023-03-06 18:33:26 --- pg_upgrade upgrade task                         begin"
                        }
               ]
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
