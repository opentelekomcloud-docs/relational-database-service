:original_name: rds_21_0004.html

.. _rds_21_0004:

Configuring the Routing Policy for a Database Proxy
===================================================

Function
--------

This API is used to configure the routing policy for a database proxy.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/proxy/{proxy_id}/route-mode

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | proxy_id              | Yes                   | Database proxy ID.                                                                               |
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

.. table:: **Table 3** Parameters

   +--------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type             | Description                                                                                                                      |
   +====================+=================+==================+==================================================================================================================================+
   | master_weight      | Yes             | Integer          | Read weight of the primary instance.                                                                                             |
   |                    |                 |                  |                                                                                                                                  |
   |                    |                 |                  | -  When **route_mode** is set to **0**, the value of this parameter ranges from 0 to 1000.                                       |
   |                    |                 |                  | -  When **route_mode** is set to a value other than 0, this parameter does not take effect.                                      |
   +--------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | readonly_instances | Yes             | Array of objects | Read weights of database nodes. For details, see :ref:`Table 4 <rds_21_0004__en-us_topic_0000001739926168_table19846103222813>`. |
   |                    |                 |                  |                                                                                                                                  |
   |                    |                 |                  | -  You can only configure weights for read replicas.                                                                             |
   |                    |                 |                  | -  This parameter can be left blank.                                                                                             |
   +--------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | route_mode         | Yes             | Integer          | Routing policy of the database proxy.                                                                                            |
   |                    |                 |                  |                                                                                                                                  |
   |                    |                 |                  | -  **0**: weighted                                                                                                               |
   |                    |                 |                  | -  **1**: load balancing (The primary instance does not process read requests.)                                                  |
   |                    |                 |                  | -  **2**: load balancing (The primary instance processes read requests.)                                                         |
   +--------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------+

.. _rds_21_0004__en-us_topic_0000001739926168_table19846103222813:

.. table:: **Table 4** readonly_instances field data structure description

   +-------------+-----------+---------+--------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                                                          |
   +=============+===========+=========+======================================================================================+
   | instance_id | Yes       | String  | Read Replica ID. For details, see :ref:`Table 9 <rds_01_0004__table15816167142613>`. |
   +-------------+-----------+---------+--------------------------------------------------------------------------------------+
   | weight      | Yes       | Integer | Read weight assigned.                                                                |
   +-------------+-----------+---------+--------------------------------------------------------------------------------------+

Example Request
---------------

Configure the routing policy for a database proxy.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/23a50154cf494ec9ad6883979a12db0a/instances/ba0fd7c13cca4655820e0f858d5d467bin01/proxy/4e2a0c70f70f4807940db73a30b5b522po01/route-mode

   {
      "master_weight" : 0,
      "readonly_instances" : [ {
        "instance_id" : "2edc88e921bb4129bb4d9b76be66811dno07",
        "weight" : 1
      } ],
      "route_mode" : 2
    }

Response
--------

-  Normal response

   .. table:: **Table 5** Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                  |
      +=======================+=======================+==============================================================+
      | result                | String                | Result of changing the routing policy of the database proxy. |
      |                       |                       |                                                              |
      |                       |                       | -  **failed**                                                |
      |                       |                       | -  **success**                                               |
      +-----------------------+-----------------------+--------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
         "result" : "success"
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
