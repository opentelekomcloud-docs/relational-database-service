:original_name: rds_05_0020.html

.. _rds_05_0020:

Changing a Floating IP Address
==============================

Function
--------

This API is used to change the floating IP address of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

The floating IP address cannot be changed if the DB instance is in any of the following statuses: creating, rebooting, upgrading, changing instance class, creating users, or deleting users.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/ip

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

.. table:: **Table 3** Parameter description

   ====== ========= ====== =================================
   Name   Mandatory Type   Description
   ====== ========= ====== =================================
   new_ip Yes       String Indicates the private IP address.
   ====== ========= ====== =================================

Example Request
---------------

Change the floating IP address of a DB instance.

.. code-block:: text

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/ip

   {
        "new_ip": "192.168.0.1"
   }

Response
--------

-  Normal response

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Name                              | Description                                                                                                                     |
   +===================================+=================================================================================================================================+
   | workflowId                        | Indicates the workflow ID.                                                                                                      |
   |                                   |                                                                                                                                 |
   |                                   | For details about how to query this parameter, see :ref:`Obtaining Information About a Task with a Specified ID <rds_13_0003>`. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
          "workflowId":"83abc7bc-2c70-4534-8565-351187b37715"
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
