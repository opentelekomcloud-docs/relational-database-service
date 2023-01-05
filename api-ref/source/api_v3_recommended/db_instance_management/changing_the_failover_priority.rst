:original_name: rds_05_0012.html

.. _rds_05_0012:

Changing the Failover Priority
==============================

Function
--------

This API is used to change the failover priority for primary/standby DB instances to meet different service requirements. You can select **Reliability First** or **Availability First**.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This API is supported for primary/standby and cluster DB instances.
-  The failover priority cannot be changed if the DB instance is in any of the following statuses: creating, upgrading, creating users, or deleting users.

URI
---

-  URI format

   PUT /v3/{*project_id*}/instances/{*instance_id*}/failover/strategy

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

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                   |
      +=================+=================+=================+===============================================================================================================================================================================================================+
      | repairStrategy  | Yes             | String          | Specifies the failover priority. Valid value:                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                               |
      |                 |                 |                 | -  **reliability**: Data reliability is preferentially ensured during the failover to minimize the amount of lost data. It is recommended for services that require high data consistency.                    |
      |                 |                 |                 | -  **availability**: Data availability is preferentially ensured during the failover to recover services quickly. It is recommended for services that have high requirements on the database online duration. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/failover/strategy

-  Request example

   .. code-block:: text

      {
           "repairStrategy": "availability"
      }

Response
--------

-  Normal response

   None

-  Example normal response

   .. code-block:: text

      {}

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
