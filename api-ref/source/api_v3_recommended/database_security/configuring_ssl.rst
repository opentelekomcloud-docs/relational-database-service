:original_name: rds_05_0017.html

.. _rds_05_0017:

Configuring SSL
===============

Secure Socket Layer (SSL) is an encryption-based Internet security protocol for establishing an encrypted link between a server and a client. It provides authenticated Internet connections to ensure the privacy and integrity of online communications. SSL:

-  Authenticates users and servers, ensuring that data is sent to the correct clients and servers.
-  Encrypts data, preventing it from being intercepted during transmission.
-  Ensures data integrity during transmission.

Clients using versions earlier than 5.1 have SSL compatibility issues. By default, SSL is disabled for new RDS for MySQL instances. If your client has no SSL compatibility issues, you can enable SSL. Enabling SSL will increase the network connection response time and CPU resource consumption. Before configuring it, evaluate any potential impacts on service performance.

Function
--------

This API is used to configure SSL to encrypt connections.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  SSL cannot be configured when a DB instance is being created, rebooted, or upgraded, its specifications are being modified, or database users are being created or deleted.

-  This API is supported for MySQL only.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/ssl

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

      +-----------------+-----------------+-----------------+----------------------------------+
      | Name            | Mandatory       | Type            | Description                      |
      +=================+=================+=================+==================================+
      | ssl_option      | Yes             | boolean         | Specifies whether to enable SSL. |
      |                 |                 |                 |                                  |
      |                 |                 |                 | -  **true**: SSL is enabled.     |
      |                 |                 |                 | -  **false**: SSL is disabled.   |
      +-----------------+-----------------+-----------------+----------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/ssl

-  Request example

   .. code-block:: text

      {
           "ssl_option": true
      }

Response
--------

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
