:original_name: rds_21_0001.html

.. _rds_21_0001:

Enabling Database Proxy
=======================

Function
--------

This API is used to enable database proxy for a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/proxy/open

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

   +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type             | Description                                                                                                                                                                                                                                        |
   +===================+=================+==================+====================================================================================================================================================================================================================================================+
   | flavor_ref        | Yes             | String           | Specification code of the database proxy.                                                                                                                                                                                                          |
   |                   |                 |                  |                                                                                                                                                                                                                                                    |
   |                   |                 |                  | -  When the site supports the database proxy in primary/standby mode, this parameter does not take effect.                                                                                                                                         |
   |                   |                 |                  | -  When the site supports the database proxy in cluster mode, set this parameter to the value of **code** in the response body in :ref:`Querying Database Proxy Specifications <rds_21_0003>`.                                                     |
   +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_num          | Yes             | Integer          | Number of database proxy nodes.                                                                                                                                                                                                                    |
   |                   |                 |                  |                                                                                                                                                                                                                                                    |
   |                   |                 |                  | -  When the site supports the database proxy in primary/standby mode, set this parameter to **2**.                                                                                                                                                 |
   |                   |                 |                  | -  When the site supports the database proxy in cluster mode, the minimum value of this parameter is **2**. For the maximum value, see the value of **max_proxy_node_num** in the response body in :ref:`Querying Database Proxies <rds_21_0002>`. |
   +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | proxy_name        | No              | String           | Name of the database proxy. Database proxies of the same type can have the same name under the same tenant.                                                                                                                                        |
   |                   |                 |                  |                                                                                                                                                                                                                                                    |
   |                   |                 |                  | The name must start with a letter and consist of 4 to 64 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed.                                                                                              |
   |                   |                 |                  |                                                                                                                                                                                                                                                    |
   |                   |                 |                  | If this parameter is not specified or the site supports only the database proxy in primary/standby mode, a random name will be generated.                                                                                                          |
   +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | proxy_mode        | No              | String           | Read/write mode of the database proxy.                                                                                                                                                                                                             |
   |                   |                 |                  |                                                                                                                                                                                                                                                    |
   |                   |                 |                  | -  **readwrite** (default value): readable and writable                                                                                                                                                                                            |
   |                   |                 |                  | -  **readonly**: read-only                                                                                                                                                                                                                         |
   +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | route_mode        | No              | Integer          | Routing policy of the database proxy.                                                                                                                                                                                                              |
   |                   |                 |                  |                                                                                                                                                                                                                                                    |
   |                   |                 |                  | -  **0**: weighted                                                                                                                                                                                                                                 |
   |                   |                 |                  | -  **1**: load balancing (The primary node does not process read requests.)                                                                                                                                                                        |
   |                   |                 |                  | -  **2**: load balancing (The primary node processes read requests.)                                                                                                                                                                               |
   +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | nodes_read_weight | Yes             | Array of objects | Read weights of database nodes. For details, see :ref:`Table 4 <rds_21_0001__en-us_topic_0000001789916316_table2261183574515>`.                                                                                                                    |
   |                   |                 |                  |                                                                                                                                                                                                                                                    |
   |                   |                 |                  | -  If **proxy_mode** is set to **readonly**, you need to configure a weight for at least one read replica.                                                                                                                                         |
   |                   |                 |                  | -  If **route_mode** is set to a value greater than 0, the weight configured for the primary instance does not take effect.                                                                                                                        |
   +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id         | No              | String           | Subnet ID in the VPC hosting the DB instance.                                                                                                                                                                                                      |
   |                   |                 |                  |                                                                                                                                                                                                                                                    |
   |                   |                 |                  | The value can be any subnet ID in the VPC to which the instance belongs. To obtain the subnet ID, go to the subnet details page on the VPC console.                                                                                                |
   +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _rds_21_0001__en-us_topic_0000001789916316_table2261183574515:

.. table:: **Table 4** nodes_read_weight field data structure description

   +-------------+-----------+---------+--------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                                                          |
   +=============+===========+=========+======================================================================================+
   | instance_id | Yes       | String  | Read Replica ID. For details, see :ref:`Table 9 <rds_01_0004__table15816167142613>`. |
   +-------------+-----------+---------+--------------------------------------------------------------------------------------+
   | weight      | Yes       | Integer | Read weight assigned.                                                                |
   +-------------+-----------+---------+--------------------------------------------------------------------------------------+

Example Request
---------------

Enable database proxy for a DB instance.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/23a50154cf494ec9ad6883979a12db0a/instances/920ec36cef814a8b830a5bed50d9a088in01/proxy/open

   {
       "flavor_ref": "rds.proxy.xlarge.2",
       "node_num": 2,
       "proxy_name": "proxy-test",
       "nodes_read_weight": [
           {
               "instance_id": "917c67424dd54af3addf537a069e5b20in01",
               "weight": 1
           }
       ]
   }

Response
--------

-  Normal response

   .. table:: **Table 5** Parameters

      ========= ====== ==================
      Parameter Type   Description
      ========= ====== ==================
      job_id    String Task ID.
      proxy_id  String Database proxy ID.
      ========= ====== ==================

-  Example normal response

   .. code-block::

      {
         "job_id" : "09908118-8e32-4742-982a-7be194f59e1d",
         "proxy_id" : "69bb32f08262418c8478ffc92f2ba1e6po01"
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
