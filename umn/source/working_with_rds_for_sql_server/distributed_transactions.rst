:original_name: rds_sqlserver_01_0001.html

.. _rds_sqlserver_01_0001:

Distributed Transactions
========================

Scenarios
---------

The participator, transaction-supported server, resource server, and transaction manager of a distributed transaction are deployed on different nodes in a distributed system. Operations contained in a transaction are considered as a logical unit, and they either succeed completely, or fail completely. Distributed transactions are used to ensure data consistency among different databases.

The Microsoft Distributed Transaction Coordinator (MSDTC) service is a component of modern versions of Microsoft Windows that is responsible for coordinating transactions that span multiple resource managers. To use distributed transactions on databases, you must enable MSDTC on each participating server. MSDTC has been enabled when you enable distributed transactions on RDS for SQL Server databases. To enable MSDTC on remote servers, see :ref:`Configuring MSDTC on a Remote Server <rds_sqlserver_01_0001__section1923413545597>`.

For more information, see `MS DTC Distributed Transactions <https://docs.microsoft.com/en-us/previous-versions/sql/sql-server-2008/ms190799(v=sql.100)>`__.

Constraints
-----------

-  Distributed transactions are enabled for newly created DB instances by default.
-  Read replicas do not support distributed transactions.
-  Once enabled, distributed transactions cannot be disabled.
-  Enabling distributed transactions will cause DB instance to reboot. Exercise caution when you perform this operation.
-  After a database link is created for a Microsoft SQL Server DB instance, if a primary/standby switchover or failover occurs, the database link will not be automatically synchronized to the new primary DB instance. You need to create a database link on the new primary DB instance again.

Enabling Distributed Transactions
---------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Distributed Transactions**. On the displayed page, click |image2| in the **Distributed Transaction** field.
#. In the displayed dialog box, click **Yes** to enable the distributed transaction function. The DB instance will be rebooted during this process.

Adding Hosts
------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Distributed Transactions**. On the displayed page, click **Add Host**.
#. In the displayed dialog box, enter host names and IP addresses, and click **Test Connection**. After all host connection tests are successful, click **OK**.

   -  Host IP name: Enter the names of the hosts for which you want to create distributed transactions with the RDS DB instance. Each host name must be unique and contains 1 to 64 characters, including only letters, digits, and hyphens (-).
   -  Host IP address: Enter the IP addresses of the hosts for which you want to create distributed transactions with the RDS DB instance. You need to configure the inbound and outbound rules in the security group for the host IP addresses first.

      .. note::

         -  If the hosts to be added are ECSs that are in the same VPC as your RDS DB instance, enter the private IP address of the ECS. You can obtain the ECS's private IP address on the ECS details page.
         -  If the hosts to be added are ECSs that are in different VPCs from the RDS DB instance, enter the public IP addresses of the ECSs. You need to bind an EIP to the RDS DB instance by referring to :ref:`Binding and Unbinding an EIP <rds_sqlserver_0025>`.

Resolving Names on Remote Servers (ECSs)
----------------------------------------

#. Log in to the management console.
#. Click |image4| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. In the navigation pane on the left, choose **Distributed Transactions**. On the displayed page, obtain information about the RDS DB instance.
#. Add the RDS DB instance information to the hosts file in **C:\\Windows\\System32\\drivers\\etc\\hosts**.

.. _rds_sqlserver_01_0001__section1923413545597:

Configuring MSDTC on a Remote Server
------------------------------------

#. Click **Start** and choose **Control Panel** > **Administrative Tools** > **Component Services**.

#. Expand the nodes in the **Console** pane Choose **Computers** > **My Computer** > **Distributed Transaction Coordinator**.

#. Right-click **Local DTC** and choose **Properties**.

#. In the displayed dialog box, click the **Security** tab. Configure information as required as shown in :ref:`Figure 1 <rds_sqlserver_01_0001__fig569033416215>` and click **OK**.

   .. _rds_sqlserver_01_0001__fig569033416215:

   .. figure:: /_static/images/en-us_image_0000001739814584.png
      :alt: **Figure 1** Local DTC properties

      **Figure 1** Local DTC properties

Deleting Hosts
--------------

#. Log in to the management console.

#. Click |image5| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Distributed Transactions**. In the host list, locate the host to be deleted and click **Delete** in the **Operation** column.

   Alternatively, select one or more hosts to be deleted and click **Delete** above the list to delete hosts in batches.

#. In the displayed dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
.. |image2| image:: /_static/images/en-us_image_0000001786853833.png
.. |image3| image:: /_static/images/en-us_image_0000001786854381.png
.. |image4| image:: /_static/images/en-us_image_0000001786854381.png
.. |image5| image:: /_static/images/en-us_image_0000001786854381.png
