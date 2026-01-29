:original_name: rds_05_0013.html

.. _rds_05_0013:

Manually Switching Primary/Standby DB Instances
===============================================

Function
--------

This API is used to manually switch primary/standby DB instances as required.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is supported for primary/standby and cluster DB instances.
-  Primary/standby DB instances cannot be manually switched if they are in any of the following statuses:

   -  For MySQL, PostgreSQL and SQLServer: creating, rebooting, upgrading, changing instance class, restoring, changing port, or creating database account

   -  For MySQL: deleting database account

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/failover

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

   None

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/failover

-  Request example

   .. code-block:: text

      {}

Response
--------

-  Normal response

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Name                              | Description                                                                                                                     |
   +===================================+=================================================================================================================================+
   | workflowId                        | Indicates the workflow ID.                                                                                                      |
   |                                   |                                                                                                                                 |
   |                                   | For details about how to query this parameter, see :ref:`Obtaining Information About a Task with a Specified ID <rds_13_0003>`. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | instanceId                        | Indicates the DB instance ID.                                                                                                   |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | nodeId                            | Indicates former slave node that becomes a master node.                                                                         |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "workflowId":"072beb09-0573-40bf-bfe8-4be5cec9e85a",
          "instanceId":"794c38e5309344818f4b33b86ebce9b4in03",
          "nodeId":"b94ba815747040f1b0d641cd13364a06no03"
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
