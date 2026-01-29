:original_name: rds_13_0003.html

.. _rds_13_0003:

Obtaining Information About a Task with a Specified ID
======================================================

Function
--------

This API is used to obtain information about a task with a specified ID in the task center.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  RDS jobs are asynchronous. After a job is generated, it takes several seconds to query the job ID.
-  This API is used to query only asynchronous tasks in the task center within one month.
-  Information of the following asynchronous tasks can be obtained: creating single or primary/standby DB instances, creating read replicas, changing single DB instances to primary/standby instances, switching primary/standby DB instances, scaling up storage space, and binding or unbinding EIPs.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/jobs?id={id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | id                    | Yes                   | Specifies the task ID.                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

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

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/jobs?id=a9767ede-fe0f-4888-9003-e843a4c90514

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      +-----------+--------+-----------------------------------------------------------------------------------------------------+
      | Parameter | Type   | Description                                                                                         |
      +===========+========+=====================================================================================================+
      | job       | Object | Indicates the task information. For details, see :ref:`Table 4 <rds_13_0003__table54571314103317>`. |
      +-----------+--------+-----------------------------------------------------------------------------------------------------+

   .. _rds_13_0003__table54571314103317:

   .. table:: **Table 4** Job field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================================================+
      | id                    | String                | Indicates the task ID.                                                                                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the task name.                                                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the task execution status.                                                                                                                                          |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | Value:                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | -  **Running**: The task is being executed.                                                                                                                                   |
      |                       |                       | -  **Completed**: The task is successfully executed.                                                                                                                          |
      |                       |                       | -  **Failed**: The task fails to be executed.                                                                                                                                 |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Indicates the creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                             |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ended                 | String                | Indicates the end time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                  |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | process               | String                | Indicates the task execution progress.                                                                                                                                        |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | .. note::                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       |    The execution progress (such as **"60"**, indicating the task execution progress is 60%) is displayed only when the task is being executed. Otherwise, **""** is returned. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance              | Object                | Indicates information of the DB instance on which the task is executed.                                                                                                       |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | For details, see :ref:`Table 5 <rds_13_0003__table4062895917262>`.                                                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | entities              | Object                | The displayed information varies depending on the tasks.                                                                                                                      |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | For details, see :ref:`Table 6 <rds_13_0003__table1014617554138>`.                                                                                                            |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | .. note::                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       |    For asynchronous tasks without the **entities** field description, **{}** is returned.                                                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | fail_reason           | String                | Indicates the error information displayed when a task failed.                                                                                                                 |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_13_0003__table4062895917262:

   .. table:: **Table 5** instances field data structure description

      ==== ====== ===============================
      Name Type   Description
      ==== ====== ===============================
      id   String Indicates the DB instance ID.
      name String Indicates the DB instance name.
      ==== ====== ===============================

   .. _rds_13_0003__table1014617554138:

   .. table:: **Table 6** entities field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================+
      | instance              | Object                | Indicates the information required for creating an instance, changing a single instance to primary/standby, or creating a read replica. |
      |                       |                       |                                                                                                                                         |
      |                       |                       | For details, see :ref:`Table 7 <rds_13_0003__table975183423611>`.                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | resource_ids          | Array of strings      | Indicates the queried resource ID.                                                                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | volume                | Object                | Indicates the resized disk information.                                                                                                 |
      |                       |                       |                                                                                                                                         |
      |                       |                       | For details, see :ref:`Table 9 <rds_13_0003__table624912591398>`.                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | public_ip             | String                | Indicates the EIP implemented by the task.                                                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | switch_strategy       | String                | Indicates the primary/standby switchover policy.                                                                                        |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_13_0003__table975183423611:

   .. table:: **Table 7** entities.instance field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                           |
      +=======================+=======================+=======================================================================================================+
      | endpoint              | String                | Indicates the DB instance connection address.                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | type                  | String                | Indicates the DB instance type.                                                                       |
      |                       |                       |                                                                                                       |
      |                       |                       | -  **Single**: single-node instance                                                                   |
      |                       |                       | -  **Ha**: primary/standby instance                                                                   |
      |                       |                       | -  **Replica**: read replica                                                                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | datastore             | Object                | Indicates the database information. For details, see :ref:`Table 8 <rds_13_0003__table173094268581>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
      | replica_of            | String                | Indicates the primary DB instance ID. This parameter is returned only when a read replica is created. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

   .. _rds_13_0003__table173094268581:

   .. table:: **Table 8** datastore field data structure description

      ======= ====== ===============================
      Name    Type   Description
      ======= ====== ===============================
      type    String Indicates the DB engine.
      version String Indicates the database version.
      ======= ====== ===============================

   .. _rds_13_0003__table624912591398:

   .. table:: **Table 9** volume field data structure description

      ============= ====== =========================================
      Name          Type   Description
      ============= ====== =========================================
      type          String Indicates the volume type.
      original_size String Indicates the original volume size in GB.
      target_size   String Indicates the target volume size in GB.
      ============= ====== =========================================

   .. note::

      In the response example, some tasks in the task center are used as examples.

-  Example normal response

   Creating a DB instance:

   .. code-block::

      {
          "job": {
              "id": "31b8ae23-c687-4d80-b7b4-42a66c9bb886",
              "name": "CreateMysqlSingleHAInstance",
              "status": "Completed",
              "created": "2018-08-06T10:41:14+0000",
              "ended": "2018-08-06T16:41:14+0000",
              "process": "",
              "instance": {
                  "id": "a48e43ff268f4c0e879652d65e63d0fbin01",
                  "name": "DO-NOT-TOUCH-mgr2-mysql-single"
              },
              "entities": {
                  "instance": {
                      "endpoint": "192.168.1.203:3306",
                      "type": "Single",
                      "datastore": {
                          "type": "mysql",
                          "version": "5.7"
                      }
                  },
                  "resource_ids": ["a48e43ff268f4c0e879652d65e63d0fbin01.vm", "a48e43ff268f4c0e879652d65e63d0fbin01.volume"]
              }
          }
      }

   Creating a read replica:

   .. code-block::

      {
          "job": {
              "id": "31b8ae23-c687-4d80-b7b4-42a66c9bb886",
              "name": " CreateMysqlReplicaInstance",
              "status": "Completed",
              "created": "2018-08-06T10:41:14+0000",
              "ended": "2018-08-06T16:41:14+0000",
              "process": "",
              "instance": {
                  "id": "288caaa9d05f4ec1a1f58de2e0945685in01",
                  "name": "mysql-replica"
              },
              "entities": {
                  "instance": {
                      "endpoint": "192.168.1.203:3306",
                      "type": "replica",
                      "datastore": {
                          "type": "mysql",
                          "version": "5.7"
                      },
                      "replica_of": "a48e43ff268f4c0e879652d65e63d0fbin01"
                  },
                  "resource_ids": ["288caaa9d05f4ec1a1f58de2e0945685in01.vm", "288caaa9d05f4ec1a1f58de2e0945685in01.volume"]
              }
          }
      }

   Binding an EIP:

   .. code-block::

      {
          "job": {
              "id": "31b8ae23-c687-4d80-b7b4-42a66c9bb886",
              "name": "MysqlBindEIP",
              "status": "Completed",
              "created": "2018-08-06T10:41:14+0000",
              "ended": "2018-08-06T16:41:14+0000",
              "process": "",
              "instance": {
                  "id": "a48e43ff268f4c0e879652d65e63d0fbin01",
                  "name": "DO-NOT-TOUCH-mgr2-mysql-single"
              },
              "entities": {
                  "public_ip": "10.10.10.1"
              }
          }
      }

   Rebooting a DB instance:

   .. code-block::

      {
          "job": {
              "id": "31b8ae23-c687-4d80-b7b4-42a66c9bb886",
              "name": " RestartMysqlInstance",
              "status": "Completed",
              "created": "2018-08-06T10:41:14+0000",
              "ended": "2018-08-06T16:41:14+0000",
              "process": "",
              "instance": {
                  "id": "a48e43ff268f4c0e879652d65e63d0fbin01",
                  "name": "DO-NOT-TOUCH-mgr2-mysql-single"
              },
              "entities": {}
          }
      }

   Task being executed:

   .. code-block::

      {
          "job": {
              "id": "31 b8ae23 - c687 - 4 d80 - b7b4 - 42 a66c9bb886",
              "name": "CreateMysqlSingleHAInstance"," status": "Running",
              "created": "2018-08-06T10:41:14+0000",
              "process": "60% ",
              "instance": {
                  "id": "a48e43ff268f4c0e879652d65e63d0fbin01",
                  "name": "DO-NOT-TOUCH-mgr2-mysql-single"
              },
              "entities": {
                  "instance": {
                      "type": "Single",
                      "datastore": {
                          "type": "mysql",
                          "version": "5.7"
                      }
                  }
              }
          }
      }

   Task fails to be executed:

   .. code-block::

      {
          "job": {
              "id": "31 b8ae23 - c687 - 4 d80 - b7b4 - 42 a66c9bb886",
              "name": "CreateMysqlSingleHAInstance",
              "status": "Failed",
              "created": "2018-08-06T10:41:14+0000",
              "ended": "2018-08-06T16:41:14+0000",
              "process": "",
              "instance": {
                  "id": "a48e43ff268f4c0e879652d65e63d0fbin01",
                  "name": "DO-NOT-TOUCH-mgr2-mysql-single"
              },
              "entities": {
                  "instance": {
                      "type": "Single",
                      "datastore": {
                          "type": "mysql",
                          "version": "5.7"
                      }
                  }
              },
              "fail_reason": "createVM failed."
          }
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
