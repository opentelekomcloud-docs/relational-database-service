:original_name: rds_11_0018.html

.. _rds_11_0018:

Configuring the Delay Threshold and Routing Policy
==================================================

After database proxy is enabled and read replicas are created, you can configure the delay threshold and routing policy as required.

.. table:: **Table 1** Read/write splitting parameters

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   +===================================+=======================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Delay Threshold                   | The maximum delay for data to be synchronized from primary DB instances to read replicas. If a read replica's delay goes beyond the configured limit, read requests will not be forwarded to this read replica to prevent prolonged data mismatches with the primary DB instance. This happens no matter what read weight the read replica has.                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                                   | In read/write splitting scenarios, the default delay threshold is 30s and the default value range is 0-7,200s. It is recommended that the threshold be greater than or equal to 30s. Traffic is not allocated to read replicas whose delay exceeds the configured threshold.                                                                                                                                                                                                          |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Read Weight Distribution          | In read/write splitting scenarios, you can configure read weights for the primary DB instance and read replicas. If no read replicas are selected for the database proxy, read/write splitting does not take effect.                                                                                                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                                   | The read weight ranges from 1 to 1,000. Read replicas with higher read weight distributions process more read requests. For example, if the read weights distributed to one primary DB instance and four read replicas are 0, 100, 200, 500, and 300, respectively, the primary DB instance does not process any read requests (write requests are still automatically routed to the primary DB instance) while the four read replicas process read requests with a ratio of 1:2:5:3. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Configuring Delay Threshold
---------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance. The **Basic Information** page is displayed.
#. In the navigation pane on the left, click **Database Proxy**.
#. In the proxy information area, click |image2| next to the **Delay Threshold** field.

Configuring Routing Policy in Single-Proxy Mode
-----------------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance. The **Basic Information** page is displayed.

#. In the navigation pane on the left, click **Database Proxy**.

#. If proxy load balancing is not enabled, click **Configure** next to the **Routing Policy** field in the proxy information area. In the displayed dialog box, configure read weights for the primary instance and read replicas.

   .. note::

      -  The system automatically distributes weights to read replicas, including read replicas created afterwards, according to the default distribution rules. If a read replica breaks down or is deleted, the weight is automatically removed. After the read replica recovers, the weight is automatically restored.
      -  If the weight of a node is set to **0**, read requests will not be routed to the node. If the weights of all nodes are set to **0**, read requests will be randomly routed to these nodes.

#. Click **OK** and view the weights on the **Database Proxy** page.

#. If proxy load balancing is enabled, click **Configure** next to the **Routing Policy** field in the proxy information area. In the displayed dialog box, set required parameters.

   Select **Load balancing** as the routing policy. Read requests will be automatically distributed to read replicas based on the number of active connections to balance the load among these read replicas.

   Set **Reads Allowed on Primary**:

   -  **Yes**: Read requests can be routed to both the primary instance and read replicas, which increases the load of the primary instance to some extent. Configure this parameter based on your workload requirements.
   -  **No**: To offload read pressure from the primary instance, read requests are only routed to read replicas.

#. Click **OK**. On the **Database Proxy** page, view the result. You can select the instances for load balancing as required.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001482124730.png
.. |image3| image:: /_static/images/en-us_image_0000001191211679.png
