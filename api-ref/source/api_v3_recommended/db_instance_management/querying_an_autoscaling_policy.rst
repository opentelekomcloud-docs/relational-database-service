:original_name: rds_05_0027.html

.. _rds_05_0027:

Querying an Autoscaling Policy
==============================

Function
--------

This API is used to query the storage autoscaling policy of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is only available to RDS for MySQL instances whose storage type is cloud SSDs or extreme SSDs and storage space is at least 40 GB.

URI
---

-  URI format

   GET /v3/{*project_id*}/instances/{*instance_id*}/disk-auto-expansion

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                      |
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

-  URI example

   GET https://rds.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/3d39c18788b54a919bab633874c159dfin011/disk-auto-expansion

Response
--------

-  Normal response

   .. table:: **Table 2** Parameters

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                            |
      +=======================+=======================+========================================================================================================================+
      | switch_option         | Boolean               | Whether autoscaling is enabled.                                                                                        |
      |                       |                       |                                                                                                                        |
      |                       |                       | -  **true**: Enabled.                                                                                                  |
      |                       |                       | -  **false**: Disabled.                                                                                                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | limit_size            | Integer               | Upper limit for autoscaling, in GB.                                                                                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
      | trigger_threshold     | Integer               | Threshold to trigger autoscaling. If the available storage drops to this threshold or 10 GB, autoscaling is triggered. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
        "switch_option" : true,
        "limit_size" : 4000,
        "trigger_threshold" : 10
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
