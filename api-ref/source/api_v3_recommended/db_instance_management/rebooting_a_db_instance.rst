:original_name: rds_06_0003.html

.. _rds_06_0003:

Rebooting a DB Instance
=======================

Function
--------

This API is used to reboot a DB instance.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

.. important::

   The RDS DB instance will be unavailable during the reboot process. Exercise caution when performing this operation.

Constraints
-----------

The DB instance cannot reboot when it is being created, scaled, backed up, restored, or its instance class or port is being changed.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/action

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/action

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

      ======= ========= ==== =============================
      Name    Mandatory Type Description
      ======= ========= ==== =============================
      restart Yes       None This parameter is left blank.
      ======= ========= ==== =============================

-  Request example

   .. code-block:: text

      {
            "restart": {}
      }

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      ====== ====== ======================
      Name   Type   Description
      ====== ====== ======================
      job_id String Indicates the task ID.
      ====== ====== ======================

-  Example normal response

   .. code-block:: text

      {
          "job_id": "2b414788a6004883a02390e2eb0ea227"
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
