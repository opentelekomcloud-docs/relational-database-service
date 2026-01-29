:original_name: rds_05_0025.html

.. _rds_05_0025:

Stopping an Instance
====================

Function
--------

This API is used to stop a pay-per-use DB instance. The instance can be stopped for up to seven days.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  If you stop a primary instance, read replicas (if there are any) will also be stopped. They are stopped for up to seven days. You cannot stop a read replica without stopping the primary instance.

-  A stopped instance will not be moved to the recycle bin after being deleted.

-  If you do not manually start your stopped DB instance after seven days, your DB instance is automatically started during the next maintenance window.

-  After an instance is stopped, the ECS is no longer billed. Other resources, including EIPs, storage resources, and backups, are still billed.

-  An instance cannot be stopped if it is in any of the following statuses:

   Creating, rebooting, scaling up, changing instance class, restoring, and changing port

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/action/shutdown

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                                              |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Instance ID.                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   None

-  Example

   POST https://rds.eu-de.otc.t-systems.com/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/5b409baece064984a1b3eef6addae50cin01/action/shutdown

-  Request example

   .. code-block:: text

      {}

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      ====== ====== ===========
      Name   Type   Description
      ====== ====== ===========
      job_id String Job ID.
      ====== ====== ===========

-  Example normal response

   .. code-block:: text

      {
          "job_id": "2b414788a6004883a02390e2eb0ea227"
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
