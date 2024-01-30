:original_name: rds_03_0060.html

.. _rds_03_0060:

Connecting to a DB Instance
===========================

An RDS DB instance can be connected through a private network or a public network.

.. table:: **Table 1** RDS connection methods

   +--------------------------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Connect Through                      | IP Address      | Scenarios                                                                                                                                                                                | Description                                                                                                                                                                                                                  |
   +======================================+=================+==========================================================================================================================================================================================+==============================================================================================================================================================================================================================+
   | :ref:`Private network <rds_02_0016>` | Floating IP     | RDS provides a floating IP address by default.                                                                                                                                           | -  Secure and excellent performance                                                                                                                                                                                          |
   |                                      |                 |                                                                                                                                                                                          | -  Recommended                                                                                                                                                                                                               |
   |                                      |                 | When your applications are deployed on an ECS that is in the same region and VPC as RDS, you are advised to use a floating IP address to connect to the RDS DB instance through the ECS. |                                                                                                                                                                                                                              |
   +--------------------------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Public network <rds_02_0051>`  | EIP             | If you cannot access an RDS DB instance through a floating IP address, bind an EIP to the DB instance and connect the DB instance to the ECS through the EIP.                            | -  A relatively lower level of security compared to other connection methods                                                                                                                                                 |
   |                                      |                 |                                                                                                                                                                                          | -  To achieve a higher transmission rate and security level, you are advised to migrate your applications to an ECS that is in the same VPC as your RDS DB instance and use a floating IP address to access the DB instance. |
   +--------------------------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   -  VPC: indicates the Virtual Private Cloud.
   -  ECS: indicates the Elastic Cloud Server.
   -  If the ECS is in the same VPC as your RDS DB instance, you do not need to apply for an EIP.

:ref:`Figure 1 <rds_03_0060__en-us_topic_0193421516_fig6120201385414>` illustrates the connection over a private network or a public network.

.. _rds_03_0060__en-us_topic_0193421516_fig6120201385414:

.. figure:: /_static/images/en-us_image_0000001739974168.png
   :alt: **Figure 1** DB instance connection

   **Figure 1** DB instance connection
