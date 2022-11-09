:original_name: rds_01_0003.html

.. _rds_01_0003:

Deleting a DB Instance
======================

Function
--------

This API is used to delete a DB instance.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   DELETE https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID compliant with the UUID format.                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      ====== ====== ===============================================
      Name   Type   Description
      ====== ====== ===============================================
      job_id String Indicates the ID of the instance deletion task.
      ====== ====== ===============================================

-  Example normal response

   .. code-block:: text

      {
          "job_id": "dff1d289-4d03-4942-8b9f-463ea07c000d"
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
