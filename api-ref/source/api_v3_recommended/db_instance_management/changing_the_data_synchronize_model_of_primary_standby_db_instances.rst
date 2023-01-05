:original_name: rds_05_0014.html

.. _rds_05_0014:

Changing the Data Synchronize Model of Primary/Standby DB Instances
===================================================================

Function
--------

This API is used to change the data synchronize model of primary/standby DB instances based on service requirements.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is supported for MySQL and PostgreSQL.
-  This API is supported for primary/standby DB instances only.
-  The synchronize model cannot be changed if the DB instance is in any of the following statuses: creating, upgrading, changing instance class, creating users, or deleting users.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/failover/mode

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                            |
      +=================+=================+=================+========================================================+
      | mode            | Yes             | String          | Specifies the synchronize model.                       |
      |                 |                 |                 |                                                        |
      |                 |                 |                 | For MySQL, the value can be any of the following:      |
      |                 |                 |                 |                                                        |
      |                 |                 |                 | -  **async**: asynchronous                             |
      |                 |                 |                 | -  **semisync**: semi-synchronous                      |
      |                 |                 |                 |                                                        |
      |                 |                 |                 | For PostgreSQL, the value can be any of the following: |
      |                 |                 |                 |                                                        |
      |                 |                 |                 | -  **async**: asynchronous                             |
      |                 |                 |                 | -  **sync**: synchronous                               |
      +-----------------+-----------------+-----------------+--------------------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/failover/mode

-  Request example

   .. code-block:: text

      {
          "mode": "semisync"
      }

Response
--------

-  Normal response

   +-----------------------------------+-----------------------------------------------------------------------------------------------------+
   | Name                              | Description                                                                                         |
   +===================================+=====================================================================================================+
   | workflowId                        | Indicates the workflow ID.                                                                          |
   |                                   |                                                                                                     |
   |                                   | For details about how to query this parameter, see :ref:`Obtaining Task Information <rds_01_0009>`. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------+
   | instanceId                        | Indicates the DB instance ID.                                                                       |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------+
   | replicationMode                   | Indicates the replication mode.                                                                     |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "instanceId": "c8a7d0abe94840dda99bc437e9442982in01",
          "replicationMode": "semisync",
          "workflowId": "7b55d6ca-dc8e-4844-a9da-6c53a1506db3"
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
