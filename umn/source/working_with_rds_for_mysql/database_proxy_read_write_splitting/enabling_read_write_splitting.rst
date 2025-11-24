:original_name: rds_11_0017.html

.. _rds_11_0017:

Enabling Read/Write Splitting
=============================

Read/write splitting enables read and write requests to be automatically routed through a read/write splitting address. This section describes how to enable read/write splitting.

Enabling a Single Proxy
-----------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance. The **Overview** page is displayed.

#. In the navigation pane on the left, choose **Database Proxy**.

   Alternatively, in the **Connectivity** area on the **Overview** page, click **Configure** in the **Read/Write Splitting Address** field.

#. On the displayed page, click **Create Database Proxy**.

#. Configure parameters and click **Next**.

   .. table:: **Table 1** Parameter description

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================================================================================+
      | Proxy Name                        | Set the proxy name based on service requirements.                                                                                                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Role                              | -  **Read/write:** Read and write requests are split.                                                                                                                                                                                                                                         |
      |                                   | -  **Read-only:** The proxy is not connected to your primary instance and cannot receive write requests.                                                                                                                                                                                      |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Routing Policy                    | -  **Weighted**: You can change the weights of your DB instance and read replicas after read/write splitting is enabled.                                                                                                                                                                      |
      |                                   | -  **Load balancing**: This policy is only available if proxy load balancing is enabled. After **Load balancing** is selected, read requests are automatically distributed to multiple read replicas based on the number of active connections to balance the load among these read replicas. |
      |                                   |                                                                                                                                                                                                                                                                                               |
      |                                   | You can change the routing policy after the database proxy is created. For details, see :ref:`Configuring the Delay Threshold and Routing Policy <rds_11_0018>`.                                                                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Reads Allowed on Primary          | This parameter is only available if **Load balancing** is selected.                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                               |
      |                                   | -  **Yes**: Read requests can be routed to both the primary instance and read replicas.                                                                                                                                                                                                       |
      |                                   | -  **No**: Read requests are routed only to read replicas to offload read pressure from the primary instance.                                                                                                                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | New Instance Class                | Select specifications for the proxy instance based on service demands. You can change the specifications after the proxy instance is created. For details, see :ref:`Changing the Instance Class of a DB Proxy Instance <rds_11_0028>`.                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Proxy Nodes                       | Enter an integer from 2 to 8. You can change the nodes after the proxy instance is created.                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                               |
      |                                   | You are advised to set proxy nodes to the quantity of read replicas, with one proxy node for one read replica.                                                                                                                                                                                |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   -  Read/write splitting maintains database connectivity but splits read and write requests. If read/write splitting is enabled, an additional address called a read/write splitting address is provided. To use read/write splitting, switch your applications to this address.

   -  Read/write splitting address: You can connect to databases through the read/write splitting address, with read and write requests distributed to different databases automatically.

      The read/write splitting address and the floating IP address of the primary DB instance are in the same VPC and subnet and are independent from each other.

   -  Delay threshold: You can set the delay threshold after read/write splitting is enabled. For details, see :ref:`Configuring the Delay Threshold and Routing Policy <rds_11_0018>`.

   -  DB instances for load balancing: You can select DB instances for load balancing after read/write splitting is enabled.

#. Confirm the database proxy configuration.

   -  To modify the configuration, click **Previous**.
   -  If there is no need to change the settings, click **Submit**.

#. View and manage the proxy on the **Database Proxy** page.

   You can view the read/write splitting address on the **Overview** page. Read and write requests can be split through the read/write splitting address.

   The read/write splitting address and the floating IP address of the DB instance are in the same VPC and subnet and are independent from each other.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
