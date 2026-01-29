:original_name: rds_13_0002.html

.. _rds_13_0002:

Querying Instant Tasks
======================

Function
--------

This API is used to query instant tasks.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{*project_id*}/tasklist?offset={offset}&limit={limit}&id={id}&instance_id={instance_id}&order_id={order_id}&name={name}&status={status}&start_time={start_time}&end_time={end_time}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================================================================================================================+
      | project_id      | Yes             | String          | Specifies the project ID of a tenant in a region.                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                     |
      |                 |                 |                 | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.                                                                                                                                                    |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Specifies the index position. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value must be a positive number. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Specifies the number of records to be queried. The default value is **10**. The value cannot be a negative number. The minimum value is **1** and the maximum value is **50**.                                                                      |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id              | No              | String          | Task ID, which can be used for filtering.                                                                                                                                                                                                           |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id     | No              | String          | Instance ID, which can be used for filtering.                                                                                                                                                                                                       |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | order_id        | No              | String          | Order ID, which can be used for filtering.                                                                                                                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | No              | String          | Task name, which can be used for filtering.                                                                                                                                                                                                         |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status          | No              | String          | Task status, which can be used for filtering.                                                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                                     |
      |                 |                 |                 | -  **Running**: The task is running.                                                                                                                                                                                                                |
      |                 |                 |                 | -  **Completed**: The task is complete.                                                                                                                                                                                                             |
      |                 |                 |                 | -  **Failed**: The task failed.                                                                                                                                                                                                                     |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time      | No              | String          | Task start time, which can be used for filtering.                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                     |
      |                 |                 |                 | Start time in the UNIX timestamp format. The unit is millisecond and the time zone is UTC.                                                                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time        | No              | String          | Task end time, which can be used for filtering.                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                     |
      |                 |                 |                 | End time in the UNIX timestamp format. The unit is millisecond and the time zone is UTC.                                                                                                                                                            |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   .. code-block:: text

      GET https://rds.eu-de.otc.t-systems.com/v3/54623db08b174c858ba779d2aa7923a3/tasklist?offset=1&limit=3&start_time=1747919701390&end_time=1748524501390

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      +-------------+------------------+------------------------------------------------------------------------------------------------------------+
      | Parameter   | Type             | Description                                                                                                |
      +=============+==================+============================================================================================================+
      | total_count | Integer          | Total number of tasks.                                                                                     |
      +-------------+------------------+------------------------------------------------------------------------------------------------------------+
      | actions     | Array of strings | List of task names.                                                                                        |
      +-------------+------------------+------------------------------------------------------------------------------------------------------------+
      | tasks       | Array of objects | Task list. For details, see :ref:`Table 4 <rds_13_0002__en-us_topic_0000002351914973_table1379213118720>`. |
      +-------------+------------------+------------------------------------------------------------------------------------------------------------+

   .. _rds_13_0002__en-us_topic_0000002351914973_table1379213118720:

   .. table:: **Table 4** Tasks field description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | id                    | String                | Task ID.                                                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Task name.                                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | instance_id           | String                | Instance ID.                                                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | instance_name         | String                | Instance name.                                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | instance_status       | String                | Instance status.                                                                                                   |
      |                       |                       |                                                                                                                    |
      |                       |                       | -  **BUILD**: The instance is being created.                                                                       |
      |                       |                       | -  **CREATE FAIL**: The instance failed to be created.                                                             |
      |                       |                       | -  **ACTIVE**: The instance is normal.                                                                             |
      |                       |                       | -  **FAILED**: The instance is abnormal.                                                                           |
      |                       |                       | -  **FROZEN**: The instance is frozen.                                                                             |
      |                       |                       | -  **MODIFYING**: The instance is being scaled up.                                                                 |
      |                       |                       | -  **REBOOTING**: The instance is being rebooted.                                                                  |
      |                       |                       | -  **RESTORING**: The instance is being restored.                                                                  |
      |                       |                       | -  **MODIFYING INSTANCE TYPE**: The instance is being changed to primary/standby.                                  |
      |                       |                       | -  **SWITCHOVER**: A primary/standby switchover is being performed.                                                |
      |                       |                       | -  **MIGRATING**: The instance is being migrated.                                                                  |
      |                       |                       | -  **BACKING UP**: The instance is being backed up.                                                                |
      |                       |                       | -  **MODIFYING DATABASE PORT**: The database port is being changed.                                                |
      |                       |                       | -  **STORAGE FULL**: The instance storage is full.                                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | order_id              | String                | Order ID.                                                                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | process               | String                | Task progress, in percentage.                                                                                      |
      |                       |                       |                                                                                                                    |
      |                       |                       | If the task is in the **Completed** or **Failed** status, the value is an empty string.                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | fail_reason           | String                | Failure cause.                                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | create_time           | String                | Task creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                           |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | end_time              | String                | Planned task end time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                        |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Task status.                                                                                                       |
      |                       |                       |                                                                                                                    |
      |                       |                       | -  **Running**: The task is running.                                                                               |
      |                       |                       | -  **Completed**: The task is complete.                                                                            |
      |                       |                       | -  **Failed**: The task failed.                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
        "tasks" : [ {
          "id" : "676e9f17f9b74289883a44a47b8101f5",
          "name" : "RestoreSqlserverInInstance",
          "instance_id" : "4d00c7e9d22145deb889937a72b59c8ein01",
          "instance_name" : "rds-local-scale",
          "instance_status" : "FAILED",
          "order_id" : "",
          "process" : "",
          "create_time" : "2020-07-15T07:46:10+0000",
          "end_time" : "2020-07-15T09:46:10+0000",
          "status" : "Completed"
        } ],
        "actions" : [ "RestoreSqlserverInInstance" ],
        "total_count" : 1
      }

-  Abnormal Response

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
