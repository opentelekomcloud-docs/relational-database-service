:original_name: rds_05_0023.html

.. _rds_05_0023:

Modifying a Private Domain Name
===============================

Function
--------

This API is used to modify a private domain name.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   PUT /v3/{project_id}/instances/{instance_id}/modify-dns

-  Parameter description

   .. table:: **Table 1** URI Parameters

      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                           |
      +=======================+=======================+=======================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                   |
      |                       |                       |                                                                       |
      |                       |                       | To obtain the value, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                         |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | Content-Type    | Yes             | String          | The content type.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The default value is **application/json**.                                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                               |
   +=================+=================+=================+===========================================================================================================+
   | dns_name        | Yes             | String          | Specifies the prefix of the new domain name.                                                              |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | The value contains 8 to 63 characters. Only uppercase letters, lowercase letters, and digits are allowed. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

Example Request
---------------

Modify the private domain name of a DB Instance.

.. code-block:: text

   PUT https://rds.eu-de.otc.t-systems.com/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/5b409baece064984a1b3eef6addae50cin01/modify-dns
   {
        "dns_name": "testModifyDnsNewName"
   }

Response
--------

-  Normal response

   .. table:: **Table 4** Response body parameters

      +-----------+--------+-------------------------------------------------------------------+
      | Parameter | Type   | Description                                                       |
      +===========+========+===================================================================+
      | job_id    | String | Indicates the ID of the task for modifying a private domain name. |
      +-----------+--------+-------------------------------------------------------------------+

-  Normal response

   .. code-block::

      {
          "job_id": "b9e057a0-f0fb-4987-9d21-f3a7550b32e7"
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

-  Normal

   202

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
