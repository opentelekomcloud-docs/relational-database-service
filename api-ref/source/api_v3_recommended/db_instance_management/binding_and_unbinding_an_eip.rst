:original_name: rds_05_0009.html

.. _rds_05_0009:

Binding and Unbinding an EIP
============================

Function
--------

This API is used to bind an EIP to a DB instance for public access or unbind an EIP from the DB instance as required.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

An EIP cannot be bound to or unbound from a DB instance that is being created, modified, restored, or rebooted.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/public-ip

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

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                         |
      +=================+=================+=================+=====================================================================================+
      | public_ip       | No              | String          | .. important::                                                                      |
      |                 |                 |                 |                                                                                     |
      |                 |                 |                 |    NOTICE:                                                                          |
      |                 |                 |                 |    When **is_bind** is **true**, **public_ip** is mandatory.                        |
      |                 |                 |                 |                                                                                     |
      |                 |                 |                 | Specifies the EIP to be bound. The value must be in the standard IP address format. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
      | public_ip_id    | No              | String          | .. important::                                                                      |
      |                 |                 |                 |                                                                                     |
      |                 |                 |                 |    NOTICE:                                                                          |
      |                 |                 |                 |    When **is_bind** is **true**, **public_ip_id** is mandatory.                     |
      |                 |                 |                 |                                                                                     |
      |                 |                 |                 | Specifies the EIP ID. The value must be in the standard UUID format.                |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
      | is_bind         | Yes             | Boolean         | -  **true**: Bind an EIP.                                                           |
      |                 |                 |                 | -  **false**: Unbind an EIP.                                                        |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/public-ip

-  Request example

   .. code-block:: text

      {
          "public_ip":"10.145.51.214",
          "public_ip_id":"8403e9cd-a7fa-4288-8b15-c7ceac1etest",
          "is_bind":true
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
