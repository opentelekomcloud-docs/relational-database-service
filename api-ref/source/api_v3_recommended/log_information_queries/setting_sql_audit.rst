:original_name: rds_log_0001.html

.. _rds_log_0001:

Setting SQL Audit
=================

Function
--------

This API is used to set a policy for SQL audit logs.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is supported for MySQL only.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/auditlog-policy

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

      +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
      | Name              | Mandatory       | Type            | Description                                                                                                |
      +===================+=================+=================+============================================================================================================+
      | keep_days         | Yes             | Integer         | Specifies the number of days for storing audit logs. The value range is from 0 to 732.                     |
      |                   |                 |                 |                                                                                                            |
      |                   |                 |                 | -  **0**: indicates that SQL audit is disabled.                                                            |
      |                   |                 |                 | -  **1** to **732**: indicates the retention days for audit logs after SQL audit is enabled.               |
      +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
      | reserve_auditlogs | No              | Boolean         | This parameter is valid only when SQL audit is disabled.                                                   |
      |                   |                 |                 |                                                                                                            |
      |                   |                 |                 | -  **true** (default value): indicates that historical audit logs are retained when SQL audit is disabled. |
      |                   |                 |                 | -  **false**: indicates that existing historical audit logs are deleted when SQL audit is disabled.        |
      +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/auditlog-policy

-  Request example

   **Update the policy for SQL audit logs:**

   .. code-block:: text

      {
          "keep_days":5
      }

   **Disable the policy for SQL audit logs:**

   .. code-block:: text

      {
          "keep_days":0,
          "reserve_auditlogs":false
      }

Response
--------

-  Normal response

   None

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
