:original_name: rds_13_0001.html

.. _rds_13_0001:

Querying Scheduled Tasks
========================

Function
--------

This API is used to query scheduled tasks.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{*project_id*}/schedule-tasks?offset={offset}&limit={limit}&instance_name={instance_name}&instance_id={instance_id}&status={status}&start_time={start_time}&end_time={end_time}

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
      | instance_id     | No              | String          | Instance ID, which can be used for filtering.                                                                                                                                                                                                       |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_name   | No              | String          | Instance name, which can be used for filtering.                                                                                                                                                                                                     |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status          | No              | String          | Task status, which can be used for filtering.                                                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                                     |
      |                 |                 |                 | -  **Initing**: The task is being initialized.                                                                                                                                                                                                      |
      |                 |                 |                 | -  **Pending**: The task is pending.                                                                                                                                                                                                                |
      |                 |                 |                 | -  **Running**: The task is running.                                                                                                                                                                                                                |
      |                 |                 |                 | -  **Completed**: The task is complete.                                                                                                                                                                                                             |
      |                 |                 |                 | -  **Failed**: The task failed.                                                                                                                                                                                                                     |
      |                 |                 |                 | -  **Unauthorized**: The task is unauthorized.                                                                                                                                                                                                      |
      |                 |                 |                 | -  **Canceled**: The task is canceled.                                                                                                                                                                                                              |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time      | No              | String          | Task start time.                                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                     |
      |                 |                 |                 | Start time in the UNIX timestamp format. The unit is millisecond and the time zone is UTC.                                                                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time        | No              | String          | Task end time.                                                                                                                                                                                                                                      |
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

      GET https://rds.eu-de.otc.t-systems.com/v3/54623db08b174c858ba779d2aa7923a3/schedule-tasks?offset=1&limit=3&instance_id=43e4feaab48f11e89039fa163ebaa7e4in04&instance_name=sqlserver_instance&start_time=1747919701390&end_time=1748524501390

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      +----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
      | Name           | Type             | Description                                                                                                          |
      +================+==================+======================================================================================================================+
      | schedule_tasks | Array of objects | Scheduled task list. For details, see :ref:`Table 4 <rds_13_0001__en-us_topic_0000002351914973_table1379213118720>`. |
      +----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
      | total_count    | Integer          | Total number of tasks.                                                                                               |
      +----------------+------------------+----------------------------------------------------------------------------------------------------------------------+

   .. _rds_13_0001__en-us_topic_0000002351914973_table1379213118720:

   .. table:: **Table 4** schedule_tasks field description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                            |
      +=======================+=======================+========================================================================================================================+
      | id                    | String                | Task ID.                                                                                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Task name.                                                                                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | String                | Instance ID.                                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | instance_name         | String                | Instance name.                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | instance_status       | String                | Instance status.                                                                                                       |
      |                       |                       |                                                                                                                        |
      |                       |                       | -  **BUILD**: The instance is being created.                                                                           |
      |                       |                       | -  **CREATE FAIL**: The instance failed to be created.                                                                 |
      |                       |                       | -  **ACTIVE**: The instance is normal.                                                                                 |
      |                       |                       | -  **FAILED**: The instance is abnormal.                                                                               |
      |                       |                       | -  **FROZEN**: The instance is frozen.                                                                                 |
      |                       |                       | -  **MODIFYING**: The instance is being scaled up.                                                                     |
      |                       |                       | -  **REBOOTING**: The instance is being rebooted.                                                                      |
      |                       |                       | -  **RESTORING**: The instance is being restored.                                                                      |
      |                       |                       | -  **MODIFYING INSTANCE TYPE**: The instance is being changed to primary/standby.                                      |
      |                       |                       | -  **SWITCHOVER**: A primary/standby switchover is being performed.                                                    |
      |                       |                       | -  **MIGRATING**: The instance is being migrated.                                                                      |
      |                       |                       | -  **BACKING UP**: The instance is being backed up.                                                                    |
      |                       |                       | -  **MODIFYING DATABASE PORT**: The database port is being changed.                                                    |
      |                       |                       | -  **STORAGE FULL**: The instance storage is full.                                                                     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                | Project ID.                                                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | create_time           | String                | Task creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                               |
      |                       |                       |                                                                                                                        |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | start_time            | String                | Planned task start time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                          |
      |                       |                       |                                                                                                                        |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | end_time              | String                | Planned task end time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                            |
      |                       |                       |                                                                                                                        |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | order                 | String                | Task priority.                                                                                                         |
      |                       |                       |                                                                                                                        |
      |                       |                       | An integer ranging from 1 to 100. A smaller value indicates a higher priority.                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Task status.                                                                                                           |
      |                       |                       |                                                                                                                        |
      |                       |                       | -  **Initing**: The task is being initialized.                                                                         |
      |                       |                       | -  **Pending**: The task is pending.                                                                                   |
      |                       |                       | -  **Running**: The task is running.                                                                                   |
      |                       |                       | -  **Completed**: The task is complete.                                                                                |
      |                       |                       | -  **Failed**: The task failed.                                                                                        |
      |                       |                       | -  **Unauthorized**: The task is unauthorized.                                                                         |
      |                       |                       | -  **Canceled**: The task is canceled.                                                                                 |
      |                       |                       | -  **Deleted**: The task is deleted.                                                                                   |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | datastore_type        | String                | Database type.                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | volume_type           | String                | Storage type.                                                                                                          |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | target_config         | object                | Target configuration. For details, see :ref:`Table 5 <rds_13_0001__en-us_topic_0000002351914973_table18585181819340>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+

   .. _rds_13_0001__en-us_topic_0000002351914973_table18585181819340:

   .. table:: **Table 5** target_config

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                  |
      +=======================+=======================+==============================================================================================+
      | flavor                | String                | Instance class.                                                                              |
      |                       |                       |                                                                                              |
      |                       |                       | If **name** is set to **RESIZE_FLAVOR**, this parameter indicates the target instance class. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
      | cpu                   | String                | Instance vCPUs.                                                                              |
      |                       |                       |                                                                                              |
      |                       |                       | If **name** is set to **RESIZE_FLAVOR**, this parameter indicates the target vCPUs.          |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
      | mem                   | String                | Instance memory.                                                                             |
      |                       |                       |                                                                                              |
      |                       |                       | If **name** is set to **RESIZE_FLAVOR**, this parameter indicates the target memory.         |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
        "schedule_tasks" : [
      {
          "id" : "5ed6a9e95f2747f7bac1b5899ddd1316",
          "instance_id" : "3d2929b2c7ea4fe9bd27f21061d037ccin01",
          "instance_name" : "rds-zfs-test-56-44",
          "instance_status" : "ACTIVE",
          "project_id" : "54623db08b174c858ba779d2aa7923a3",
          "name" : "RESIZE_FLAVOR",
          "create_time" : "2020-07-15T07:46:10+0000",
          "start_time" : "2020-07-15T08:46:10+0000",
          "end_time" : "2020-07-15T09:46:10+0000",
          "order" : "1",
          "status" : "Canceled",
          "datastore_type" : "mysql",
          "target_config" : {
            "flavor" : "rds.mysql.n1.xlarge.2",
            "mem" : "8",
            "cpu" : "4"
          },
          "volume_type" : "CLOUDSSD"
        } ],
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
