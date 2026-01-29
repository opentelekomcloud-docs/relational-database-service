:original_name: rds_05_0022.html

.. _rds_05_0022:

Applying for a Private Domain Name
==================================

Function
--------

This API is used to bind a private domain name to a specified DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   POST /v3/{project_id}/instances/{instance_id}/create-dns

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

   +-----------+-----------+--------+---------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                               |
   +===========+===========+========+===========================================================================+
   | dns_type  | Yes       | String | Specifies the domain name type. Currently, only **private** is supported. |
   +-----------+-----------+--------+---------------------------------------------------------------------------+

Example Request
---------------

Apply for a private domain name.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/5b409baece064984a1b3eef6addae50cin01/create-dns
   {
        "dns_type": "private"
   }

Response
--------

-  Normal response

   .. table:: **Table 4** Response body parameters

      +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Type   | Description                                                                                                                                                                                       |
      +===========+========+===================================================================================================================================================================================================+
      | job_id    | String | Indicates the ID of the task for applying for a private domain name. To query actual status of the running task, see :ref:`Obtaining Information About a Task with a Specified ID <rds_13_0003>`. |
      +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
