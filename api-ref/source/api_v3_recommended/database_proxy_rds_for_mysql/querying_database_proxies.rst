:original_name: rds_21_0002.html

.. _rds_21_0002:

Querying Database Proxies
=========================

Function
--------

This API is used to query database proxies of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/proxy-list

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

-  Request parameters

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  URI example

   .. code-block:: text

      GET https://rds.eu-de.otc.t-systems.com/v3/23a50154cf494ec9ad6883979a12db0a/instances/920ec36cef814a8b830a5bed50d9a088in01/proxy-list

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      +------------------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | Parameter                                      | Type                  | Description                                                                                     |
      +================================================+=======================+=================================================================================================+
      | proxy_query_info_list                          | Array of objects      | List of database proxies under a DB instance.                                                   |
      |                                                |                       |                                                                                                 |
      |                                                |                       | For details, see :ref:`Table 4 <rds_21_0002__en-us_topic_0000001787045181_table1950773843311>`. |
      +------------------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | max_proxy_num                                  | Integer               | Maximum number of database proxies that can be enabled at the same time.                        |
      +------------------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | max_proxy_node_num                             | Integer               | Maximum number of nodes allowed for one database proxy.                                         |
      +------------------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | support_balance_route_mode_for_favored_version | Boolean               | Whether load balancing can be configured when a database proxy is created.                      |
      +------------------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+

   .. _rds_21_0002__en-us_topic_0000001787045181_table1950773843311:

   .. table:: **Table 4** proxy_query_info_list field data structure description

      +-----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | Parameter                         | Type                  | Description                                                                                     |
      +===================================+=======================+=================================================================================================+
      | proxy                             | Object                | Database proxy information.                                                                     |
      |                                   |                       |                                                                                                 |
      |                                   |                       | For details, see :ref:`Table 5 <rds_21_0002__en-us_topic_0000001787045181_table1385912681212>`. |
      +-----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | master_instance                   | Object                | Primary instance information.                                                                   |
      |                                   |                       |                                                                                                 |
      |                                   |                       | For details, see :ref:`Table 8 <rds_21_0002__en-us_topic_0000001787045181_table156019539158>`.  |
      +-----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | readonly_instances                | Array of objects      | Read replica information.                                                                       |
      |                                   |                       |                                                                                                 |
      |                                   |                       | For details, see :ref:`Table 8 <rds_21_0002__en-us_topic_0000001787045181_table156019539158>`.  |
      +-----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | proxy_security_group_check_result | Boolean               | Whether the security group allows the database proxy to access the DB instance.                 |
      +-----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------+

   .. _rds_21_0002__en-us_topic_0000001787045181_table1385912681212:

   .. table:: **Table 5** proxy field data structure description

      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Parameter                           | Type                  | Description                                                                                                        |
      +=====================================+=======================+====================================================================================================================+
      | pool_id                             | String                | Database proxy ID.                                                                                                 |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | status                              | String                | Database proxy status.                                                                                             |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | -  **ENABLING**: The database proxy is being enabled.                                                              |
      |                                     |                       | -  **DISABLING**: The database proxy is being disabled.                                                            |
      |                                     |                       | -  **CHANGING_NODE_NUM**: The number of nodes is being changed for the database proxy.                             |
      |                                     |                       | -  **SCALING**: The specifications of the database proxy are being changed.                                        |
      |                                     |                       | -  **UPGRADING**: The kernel version of the database proxy is being upgraded.                                      |
      |                                     |                       | -  **IPMODIFYING**: The read/write splitting address of the database proxy is being changed.                       |
      |                                     |                       | -  **RESTARTING**: The database proxy is being restarted.                                                          |
      |                                     |                       | -  **TRANSACTION_SPLITTING**: Transaction splitting is being enabled or disabled for the database proxy.           |
      |                                     |                       | -  **CONNECTION_POOL_SWITCH_OPERATING**: The session connection pool type is being changed for the database proxy. |
      |                                     |                       | -  **PORT_MODIFYING**: The port of the database proxy is being changed.                                            |
      |                                     |                       | -  **PROXY_SSL_SWITCHING**: The SSL status is being changed for the database proxy.                                |
      |                                     |                       | -  **ALT_SWITCH_OPERATING**: The ALT status is being changed for the database proxy.                               |
      |                                     |                       | -  **CHANGING_RESOURCES**: Resources are being changed for the database proxy.                                     |
      |                                     |                       | -  **NORMAL**: The database proxy is running properly.                                                             |
      |                                     |                       | -  **ABNORMAL**: The database proxy is not running properly.                                                       |
      |                                     |                       | -  **FAILED**: The database proxy failed to be created.                                                            |
      |                                     |                       | -  **FROZEN**: The database proxy is frozen.                                                                       |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | address                             | String                | Read/write splitting address.                                                                                      |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | port                                | Integer               | Port number.                                                                                                       |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | delay_threshold_in_seconds          | Integer               | Delay threshold, in seconds.                                                                                       |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | cpu                                 | String                | vCPUs of the database proxy.                                                                                       |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | mem                                 | String                | Memory size of the database proxy.                                                                                 |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | node_num                            | Integer               | Number of database proxy nodes.                                                                                    |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | nodes                               | Array of objects      | List of database proxy nodes.                                                                                      |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | For details, see :ref:`Table 6 <rds_21_0002__en-us_topic_0000001787045181_table208401591318>`.                     |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | mode                                | String                | Database proxy mode.                                                                                               |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | -  **Cluster**                                                                                                     |
      |                                     |                       | -  **Ha**: primary/standby                                                                                         |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | flavor_info                         | Object                | Database proxy specifications.                                                                                     |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | For details, see :ref:`Table 7 <rds_21_0002__en-us_topic_0000001787045181_table711853617142>`.                     |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | transaction_split                   | String                | Status of transaction splitting for the database proxy.                                                            |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | -  **true**: enabled                                                                                               |
      |                                     |                       | -  **false**: disabled                                                                                             |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | connection_pool_type                | String                | Connection pool type.                                                                                              |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | -  **CLOSED**: The connection pool is closed.                                                                      |
      |                                     |                       | -  **SESSION**: The session-level connection pool is enabled.                                                      |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | pay_mode                            | String                | Billing mode of the database proxy.                                                                                |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | -  **0**: pay-per-use billing                                                                                      |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                                | String                | Name of the database proxy.                                                                                        |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | proxy_mode                          | String                | Read/write mode of the database proxy.                                                                             |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | -  **readwrite**: readable and writable                                                                            |
      |                                     |                       | -  **readonly**: read-only                                                                                         |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | dns_name                            | String                | Private domain name for the read/write splitting address of the database proxy.                                    |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | If this parameter is left blank, no private domain name has been requested.                                        |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | subnet_id                           | String                | ID of the subnet to which the database proxy belongs.                                                              |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | seconds_level_monitor_fun_status    | String                | Status of Monitoring by Seconds of the database proxy.                                                             |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | -  off                                                                                                             |
      |                                     |                       | -  on                                                                                                              |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | alt_flag                            | Boolean               | ALT switch status.                                                                                                 |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | force_read_only                     | Boolean               | Whether to forcibly route read requests to read replicas.                                                          |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | route_mode                          | Integer               | Routing policy of the database proxy.                                                                              |
      |                                     |                       |                                                                                                                    |
      |                                     |                       | -  **0**: weighted                                                                                                 |
      |                                     |                       | -  **1**: load balancing (The primary instance does not process read requests.)                                    |
      |                                     |                       | -  **2**: load balancing (The primary instance processes read requests.)                                           |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | ssl_option                          | Boolean               | SSL switch status.                                                                                                 |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | support_balance_route_mode          | Boolean               | Whether load balancing can be enabled for the database proxy.                                                      |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | support_proxy_ssl                   | Boolean               | Whether SSL can be enabled for the database proxy.                                                                 |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | support_switch_connection_pool_type | Boolean               | Whether the session connection pool type can be changed for the database proxy.                                    |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | support_transaction_split           | Boolean               | Whether transaction splitting can be enabled for the database proxy.                                               |
      +-------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _rds_21_0002__en-us_topic_0000001787045181_table208401591318:

   .. table:: **Table 6** nodes field data structure description

      +-----------------------+-----------------------+---------------------------------------------------+
      | Parameter             | Type                  | Description                                       |
      +=======================+=======================+===================================================+
      | id                    | String                | ID of the database proxy node.                    |
      +-----------------------+-----------------------+---------------------------------------------------+
      | status                | String                | Status of the database proxy node.                |
      |                       |                       |                                                   |
      |                       |                       | -  **NORMAL**: The node is normal.                |
      |                       |                       | -  **ABNORMAL**: The node is abnormal.            |
      |                       |                       | -  **CREATING**: The node is being created.       |
      |                       |                       | -  **CREATEFAIL**: The node failed to be created. |
      +-----------------------+-----------------------+---------------------------------------------------+
      | role                  | String                | Role of the database proxy node.                  |
      |                       |                       |                                                   |
      |                       |                       | -  **master**: primary node                       |
      |                       |                       | -  **slave**: standby node                        |
      +-----------------------+-----------------------+---------------------------------------------------+
      | az_code               | String                | AZ where the database proxy node is located.      |
      +-----------------------+-----------------------+---------------------------------------------------+
      | frozen_flag           | Integer               | Whether the database proxy node is frozen.        |
      |                       |                       |                                                   |
      |                       |                       | -  **0**: unfrozen                                |
      |                       |                       | -  **1**: frozen                                  |
      +-----------------------+-----------------------+---------------------------------------------------+

   .. _rds_21_0002__en-us_topic_0000001787045181_table711853617142:

   .. table:: **Table 7** flavor_info field data structure description

      +-----------------------+-----------------------+-----------------------+
      | Parameter             | Type                  | Description           |
      +=======================+=======================+=======================+
      | group_type            | String                | CPU architecture.     |
      |                       |                       |                       |
      |                       |                       | -  X86                |
      |                       |                       | -  ARM                |
      +-----------------------+-----------------------+-----------------------+
      | code                  | String                | Specification code.   |
      +-----------------------+-----------------------+-----------------------+

   .. _rds_21_0002__en-us_topic_0000001787045181_table156019539158:

   .. table:: **Table 8** readonly_instances field data structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | id                    | String                | ID of the primary instance or read replica.                                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | status                | String                | Node status.                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | name                  | String                | Instance name.                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | weight                | Integer               | Read weight of the instance.                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | available_zones       | Array of objects      | AZ information.                                                                                  |
      |                       |                       |                                                                                                  |
      |                       |                       | For details, see :ref:`Table 9 <rds_21_0002__en-us_topic_0000001787045181_table20247131113172>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

   .. _rds_21_0002__en-us_topic_0000001787045181_table20247131113172:

   .. table:: **Table 9** available_zones field data structure description

      =========== ====== ===============
      Parameter   Type   Description
      =========== ====== ===============
      code        String AZ code.
      description String AZ description.
      =========== ====== ===============

-  Example normal response

   .. code-block::

      {
        "proxy_query_info_list" : [ {
          "proxy" : {
            "pool_id" : "e06ecf4dfea8409690c87a9ee6582b0dpo01",
            "status" : "NORMAL",
            "address" : "192.168.0.1",
            "port" : 3306,
            "delay_threshold_in_seconds" : 30,
            "cpu" : "2",
            "mem" : "4",
            "node_num" : 2,
            "nodes" : [ {
              "id" : "3079919890f24fb8ab284571fc409058pn01",
              "status" : "NORMAL",
              "role" : "master",
              "az_code" : "aaa",
              "frozen_flag" : 0
            }, {
              "id" : "804430ac9068419fa5e49d5ca0684172pn01",
              "status" : "NORMAL",
              "role" : "master",
              "az_code" : "aaa",
              "frozen_flag" : 0
            } ],
            "mode" : "Cluster",
            "flavor_info" : {
              "group_type" : "X86",
              "code" : "rds.proxy.large.2"
            },
            "transaction_split" : "false",
            "connection_pool_type" : "CLOSED",
            "pay_mode" : "0",
            "name" : "test-hll",
            "proxy_mode" : "readwrite",
            "route_mode" : 1,
            "dns_name" : "",
            "subnet_id" : "2f75f35c-62ca-43b7-9954-8fd1e6be4641",
            "ssl_option" : false,
            "force_read_only" : false,
            "seconds_level_monitor_fun_status" : "off",
            "alt_flag" : false,
            "support_transaction_split" : true,
            "support_switch_connection_pool_type" : true,
            "support_balance_route_mode" : true,
            "support_proxy_ssl" : true
          },
          "master_instance" : {
            "id" : "920ec36cef814a8b830a5bed50d9a088in01",
            "status" : "normal",
            "name" : "rds-2c54",
            "weight" : 0,
            "available_zones" : [ {
              "code" : "aaa",
              "description" : "az3"
            } ]
          },
          "readonly_instances" : [ {
            "id" : "f9462b58982d484fb64fd9880504d863in01",
            "status" : "abnormal",
            "name" : "replica-f966",
            "weight" : 0,
            "available_zones" : [ {
              "code" : "aaa",
              "description" : "az3"
            } ]
          } ],
          "proxy_security_group_check_result" : false
        } ],
        "max_proxy_num" : 4,
        "max_proxy_node_num" : 4,
        "support_balance_route_mode_for_favored_version" : true
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
