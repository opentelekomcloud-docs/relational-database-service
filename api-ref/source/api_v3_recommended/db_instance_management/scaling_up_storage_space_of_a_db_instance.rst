:original_name: rds_01_0102.html

.. _rds_01_0102:

Scaling Up Storage Space of a DB Instance
=========================================

Function
--------

This API is used to scale up storage space of a DB instance.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The sizes of the primary and standby DB instances are the same. When you scale the primary DB instance, its standby DB instance is also scaled.
-  The DB instances can be scaled when they are in the **Available** state.

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

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                         |
      +=================+=================+=================+=====================================================================+
      | enlarge_volume  | Yes             | Object          | Specifies the target storage space after scaling up.                |
      |                 |                 |                 |                                                                     |
      |                 |                 |                 | For details, see :ref:`Table 3 <rds_01_0102__table17521151123114>`. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

   .. _rds_01_0102__table17521151123114:

   .. table:: **Table 3** enlarge_volume field data structure description

      +------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Name | Mandatory | Type    | Description                                                                                                                                 |
      +======+===========+=========+=============================================================================================================================================+
      | size | Yes       | Integer | The minimum start value of each scaling is 10 GB. A DB instance can be scaled up only by a multiple of 10 GB. Value range: 10 GB to 4000 GB |
      +------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
          "enlarge_volume": {
              "size": 400
          }
      }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

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
