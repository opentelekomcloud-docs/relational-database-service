:original_name: rds_05_0031.html

.. _rds_05_0031:

Querying the Domain Name of a DB Instance
=========================================

Function
--------

This API is used to query the domain name of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET /v3/{project_id}/instances/{instance_id}/dns

-  Parameter description

   .. table:: **Table 1** URI Parameters

      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                           |
      +=======================+=======================+=======================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                   |
      |                       |                       |                                                                       |
      |                       |                       | To obtain the value, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | instance_id           | Yes                   | Instance ID.                                                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | dns_type              | Yes                   | Domain type. Only private domains are supported.                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/c90928717dc747e2a20099894a87c468in01/dns?dns_type=private

Response
--------

-  Normal response

   .. table:: **Table 3** Response body parameters

      +-----------------------+-----------------------+-------------------------------------------------------+
      | Parameter             | Type                  | Description                                           |
      +=======================+=======================+=======================================================+
      | instance_id           | String                | Instance ID.                                          |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | dns_name              | String                | Domain name of the instance.                          |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | dns_type              | String                | Domain type. Value: **private**.                      |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | ipv4_address          | String                | Virtual IP address bound to the instance domain name. |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | status                | String                | Domain status:                                        |
      |                       |                       |                                                       |
      |                       |                       | -  normal                                             |
      |                       |                       | -  abnormal                                           |
      +-----------------------+-----------------------+-------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
          "instance_id": "2de6315e7197418fbf2fdaed59d65da1in03",
          "dns_name": "2de6315e7197418fbf2fdaed59d65da1in03.internal.eu-de-****.com",
          "dns_type": "private",
          "ipv4_address": "192.168.6.105",
          "status": "normal"
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
