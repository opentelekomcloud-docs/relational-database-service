:original_name: rds_03_0013.html

.. _rds_03_0013:

Connecting to a DB Instance Through a Private Network
=====================================================

You can connect to a DB instance through a non-SSL connection or an SSL connection. The SSL connection encrypts data and is more secure.

.. _rds_03_0013__section142821253295:

Preparations
------------

#. .. _rds_03_0013__li532714618279:

   Prepare an ECS.

   To connect to a DB instance through a private network, you must first create an ECS.

   For details about how to create an ECS, see section :ref:`How Can I Create and Connect to an ECS? <rds_faq_0057>`

   -  The ECS and RDS DB instance must be in the same VPC.
   -  The ECS must be allowed by the security group to access RDS DB instances.

      -  If the security group with which the target DB instance is associated is the default security group, you do not need to configure security group rules.
      -  If the security group with which the target DB instance is associated is not the default security group, check whether the security group rules allow the ECS to connect to the DB instance.

         a. Log in to the management console.

         b. Click |image1| in the upper left corner and select a region and a project.

         c. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

         d. On the **Instances** page, click the target DB instance.

         e. In the **Connection Information** area, click the security group to view its rules.

            If the security group rules allow the access from the ECS, the ECS can connect to the DB instance.

            If the security group rules do not allow the access from the ECS, you need to add a security group rule. For details, see section :ref:`Configuring Security Group Rules <rds_03_0005>`.

#. Install the Microsoft SQL Server client.

   Install the Microsoft SQL Server client on the ECS or device that was prepared in :ref:`1 <rds_03_0013__li532714618279>`.

   For details, see section :ref:`How Can I Install SQL Server Management Studio? <rds_faq_0032>`

Non-SSL Connection
------------------

#. Log in to the ECS or device that can access RDS.

#. Start SQL Server Management Studio.

#. Choose **Connect** > **Database Engine**. In the displayed dialog box, enter login information.


   .. figure:: /_static/images/en-us_image_0000001470140373.png
      :alt: **Figure 1** Connecting to the server

      **Figure 1** Connecting to the server

   -  **Server name**: indicates the IP address and port of the DB instance. Use a comma (,) to separate them. For example: x.x.x.x,8080.

      -  The IP address is the floating IP address in the **Connection Information** area on the **Basic Information** page of the DB instance.
      -  The port is the database port in the **Connection Information** area on the **Basic Information** page of the DB instance.

   -  **Authentication**: indicates the authentication mode. Select **SQL Server Authentication**.
   -  **Login**: indicates the RDS database username. The default administrator is **rdsuser**.
   -  **Password**: indicates the password of the RDS database username.

#. Click **Connect** to connect to the DB instance.

   .. note::

      If the connection fails, ensure that preparations have been correctly made in :ref:`Preparations <rds_03_0013__section142821253295>` and try again.

SSL Connection
--------------

#. Download the SSL root certificate and then upload it.

   a. In the **DB Information** area on the **Basic Information** page, click |image2| in the **SSL** field to download the root certificate or certificate bundle.
   b. Upload the root certificate to the ECS or save it to the device to be connected to the DB instance.
   c. Import the root certificate into the Windows OS on the ECS. For details, see :ref:`How Can I Import the Root Certificate to a Windows or Linux OS? <rds_faq_0052>`

      .. note::

         -  Replace the old certificate before it expires to improve system security.
         -  After you bind an EIP to a DB instance, you must reboot the instance for the SSL connection to take effect.

#. Start SQL Server Management Studio.

#. Choose **Connect** > **Database Engine**. In the displayed dialog box, enter login information.


   .. figure:: /_static/images/en-us_image_0000001420023666.png
      :alt: **Figure 2** Connecting to the server

      **Figure 2** Connecting to the server

   -  **Server name**: indicates the IP address and port of the DB instance. Use a comma (,) to separate them. For example: x.x.x.x,8080.

      -  The IP address is the floating IP address in the **Connection Information** area on the **Basic Information** page of the DB instance.
      -  The port is the database port in the **Connection Information** area on the **Basic Information** page of the DB instance.

   -  **Authentication**: indicates the authentication mode. Select **SQL Server Authentication**.
   -  **Login**: indicates the RDS database username. The default administrator is **rdsuser**.
   -  **Password**: indicates the password of the RDS database username.

#. On the **Connection Properties** page, enter related parameters and select **Encrypt connection** to enable SSL encryption. (By default, **Encrypt connection** is not selected. You need to select it manually.)


   .. figure:: /_static/images/en-us_image_0000001419863714.jpg
      :alt: **Figure 3** Connection properties

      **Figure 3** Connection properties

#. Click **Connect** to connect to the DB instance.

   .. note::

      If the connection fails, ensure that preparations have been correctly made in :ref:`Preparations <rds_03_0013__section142821253295>` and try again.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001420340582.png
