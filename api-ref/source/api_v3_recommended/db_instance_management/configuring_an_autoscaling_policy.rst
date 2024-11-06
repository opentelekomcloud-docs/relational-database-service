:original_name: rds_05_0028.html

.. _rds_05_0028:

Configuring an Autoscaling Policy
=================================

Function
--------

This API is used to configure autoscaling for a DB instance. You will be billed for the added storage.

If available storage drops to a specified threshold or 10 GB, your storage will autoscale by 15% (in increments of 10 GB) of your allocated storage.

Autoscaling up the storage of a read replica does not affect that of the primary instance. The new storage space of the read replica after autoscaling must be no less than that of the primary instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is only available to RDS for MySQL, Microsoft SQL Server and RDS for PostgreSQL instances whose storage type is cloud SSDs or extreme SSDs and storage space is at least 40 GB.
-  Storage autoscaling is unavailable when the instance is in any of the following statuses: changing instance class, upgrading a minor version, migrating the standby instance, and rebooting.
-  The storage space can be autoscaled up only when your instance status is **Available** or **Storage full**. The maximum allowed storage is 4,000 GB.

URI
---

-  URI format

   PUT /v3/{*project_id*}/instances/{*instance_id*}/disk-auto-expansion

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

   .. table:: **Table 2** Parameters

      +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                                   |
      +===================+=================+=================+===============================================================================================================================================================================================+
      | switch_option     | Yes             | Boolean         | Whether to enable autoscaling.                                                                                                                                                                |
      |                   |                 |                 |                                                                                                                                                                                               |
      |                   |                 |                 | -  **true**: indicates that autoscaling will be enabled.                                                                                                                                      |
      |                   |                 |                 | -  **false**: indicates that autoscaling will be disabled.                                                                                                                                    |
      +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit_size        | No              | Integer         | Upper limit for autoscaling, in GB. This parameter is mandatory when **switch_option** is set to **true**.                                                                                    |
      |                   |                 |                 |                                                                                                                                                                                               |
      |                   |                 |                 | The value ranges from 40 GB to 4,000 GB and must be no less than the current storage of the instance.                                                                                         |
      +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | trigger_threshold | No              | Integer         | Threshold to trigger autoscaling. If the available storage drops to this threshold or 10 GB, autoscaling is triggered. This parameter is mandatory when **switch_option** is set to **true**. |
      |                   |                 |                 |                                                                                                                                                                                               |
      |                   |                 |                 | Enumerated values:                                                                                                                                                                            |
      |                   |                 |                 |                                                                                                                                                                                               |
      |                   |                 |                 | -  10                                                                                                                                                                                         |
      |                   |                 |                 | -  15                                                                                                                                                                                         |
      |                   |                 |                 | -  20                                                                                                                                                                                         |
      +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  URI example

   PUT https://rds.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/3d39c18788b54a919bab633874c159dfin01/disk-auto-expansion

-  Request example

   .. code-block:: text

      {
        "switch_option" : true,
        "limit_size" : 4000,
        "trigger_threshold" : 10
      }

Response
--------

-  Example normal response

   None

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
