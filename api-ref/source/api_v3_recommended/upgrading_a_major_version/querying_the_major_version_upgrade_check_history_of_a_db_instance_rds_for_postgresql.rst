:original_name: rds_19_0004.html

.. _rds_19_0004:

Querying the Major Version Upgrade Check History of a DB Instance (RDS for PostgreSQL)
======================================================================================

Function
--------

This API is used to query the major version upgrade check history.

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

   GET /v3/{project_id}/instances/{instance_id}/major-version/inspection-histories?offset={offset}&limit={limit}&order={order}&sort_field={sort_field}&target_version={target_version}&is_available={is_available}

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
      |                 |                 |                 | -  **check_time**: check time                                                                                                                                                                                                                                  |
      |                 |                 |                 | -  **expiration_time**: expiration time                                                                                                                                                                                                                        |
      |                 |                 |                 | -  Default value: **check_time**                                                                                                                                                                                                                               |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | target_version  | String          | No              | Target version.                                                                                                                                                                                                                                                |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | is_available    | Boolean         | No              | Whether the check is valid.                                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                                |
      |                 |                 |                 | -  **true**: available                                                                                                                                                                                                                                         |
      |                 |                 |                 | -  **false**: unavailable                                                                                                                                                                                                                                      |
      |                 |                 |                 | -  Default value: **false**                                                                                                                                                                                                                                    |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  URI example

   .. code-block::

      https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/3aa441c4c98a4b36b100a7e3e87d17cein03/major-version/inspection-histories?offset=0&limit=10

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                    |
      +=======================+=======================+================================================================================================+
      | total_count           | Integer               | Total number of records.                                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
      | inspection_reports    | Array of objects      | Check report details.                                                                          |
      |                       |                       |                                                                                                |
      |                       |                       | For details, see :ref:`Table 3 <rds_19_0004__en-us_topic_0000001765882001_table580944933717>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+

   .. _rds_19_0004__en-us_topic_0000001765882001_table580944933717:

   .. table:: **Table 3** inspection_report field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                           |
      +=======================+=======================+=======================================================================================================================================================================================================+
      | id                    | String                | Check report ID.                                                                                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | check_time            | String                | Check time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | expiration_time       | String                | Expiration time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                       |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, if the time zone offset is one hour, the value of **Z** is **+0100**. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | target_version        | String                | Target version.                                                                                                                                                                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | result                | String                | Check results.                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                       |
      |                       |                       | -  **success**: The check is successful.                                                                                                                                                              |
      |                       |                       | -  **failed**: The check fails.                                                                                                                                                                       |
      |                       |                       | -  **running**: The check is in progress.                                                                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | detail                | String                | Check report details.                                                                                                                                                                                 |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
               "total_count": 1,
               "inspection_reports": [
                        {
                                  "id": "289903e1-3006-19e9-e054-5fb7fe376552",
                                  "check_time": "2023-03-06T02:33:49+0800",
                                  "expiration_time": "2023-03-07T02:33:49+0800",
                                  "target_version": "14.4",
                                  "result": "success",
                                  "detail": "2023-03-06 18:33:26 --- pg_upgrade check task                              begin\n2023-03-06 18:34:40 --- pg_upgrade check on master:                       [user_check_report]User check success"
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
