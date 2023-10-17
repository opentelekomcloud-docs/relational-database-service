:original_name: rds_03_0007.html

.. _rds_03_0007:

Connecting to a DB Instance Through a Public Network
====================================================

You can connect to a DB instance through a non-SSL connection or an SSL connection. The SSL connection encrypts data and is more secure.

.. _rds_03_0007__section367520762117:

Preparations
------------

#. Install the Microsoft SQL Server client.

   For details, see section :ref:`How Can I Install SQL Server Management Studio? <rds_faq_0032>`

#. Bind an EIP to the target DB instance and configure security group rules.

   a. .. _rds_03_0007__li1728416257345:

      Bind an EIP to the target DB instance.

      For details about how to bind an EIP, see section :ref:`Binding an EIP <rds_03_0006>`.

   b. .. _rds_03_0007__li85977812411:

      Obtain the IP address of the local device.

   c. Configure security group rules.

      Add the IP address obtained in :ref:`2.b <rds_03_0007__li85977812411>` and the instance port to the inbound rule of the security group.

      For details about how to configure a security group rule, see section :ref:`Configuring Security Group Rules <rds_03_0051>`.

   d. Run the **ping** command to connect the EIP that has been bound to the target DB instance in :ref:`2.a <rds_03_0007__li1728416257345>` to check that the local device can connect to the EIP.

Non-SSL Connection
------------------

#. Start SQL Server Management Studio.

#. Choose **Connect** > **Database Engine**. In the displayed dialog box, enter login information.


   .. figure:: /_static/images/en-us_image_0000001191211449.png
      :alt: **Figure 1** Connecting to the server

      **Figure 1** Connecting to the server

   -  **Server name**: indicates the IP address and port of the DB instance. Use a comma (,) to separate them. For example: x.x.x.x,8080.

      -  The IP address is the EIP that has been bound to the DB instance.
      -  The port is the database port in the **Connection Information** area on the **Basic Information** page of the DB instance.

   -  **Authentication**: indicates the authentication mode. Select **SQL Server Authentication**.
   -  **Login**: indicates the RDS database username. The default administrator is **rdsuser**.
   -  **Password**: indicates the password of the RDS database username.

#. Click **Connect** to connect to the DB instance.

   .. note::

      If the connection fails, ensure that preparations have been correctly made in :ref:`Preparations <rds_03_0007__section367520762117>` and try again.

SSL Connection
--------------

#. Download the SSL root certificate and then upload it.

   a. In the **DB Information** area on the **Basic Information** page, click |image1| in the **SSL** field to download the root certificate or certificate bundle.
   b. Upload the root certificate to the ECS to be connected to the DB instance.
   c. Import the root certificate to the Windows OS on the ECS. For details, see :ref:`How Can I Import the Root Certificate to a Windows or Linux OS? <rds_faq_0052>`

      .. note::

         -  Replace the old certificate before it expires to improve system security.
         -  After you bind an EIP to a DB instance, you must reboot the instance for the SSL connection to take effect.

#. Start SQL Server Management Studio.

#. Choose **Connect** > **Database Engine**. In the displayed dialog box, enter login information.


   .. figure:: /_static/images/en-us_image_0000001145051612.png
      :alt: **Figure 2** Connecting to the server

      **Figure 2** Connecting to the server

   -  **Server name**: indicates the IP address and port of the DB instance. Use a comma (,) to separate them. For example: x.x.x.x,8080.

      -  The IP address is the EIP that has been bound to the DB instance.
      -  The port is the database port in the **Connection Information** area on the **Basic Information** page of the DB instance.

   -  **Authentication**: indicates the authentication mode. Select **SQL Server Authentication**.
   -  **Login**: indicates the RDS database username. The default administrator is **rdsuser**.
   -  **Password**: indicates the password of the RDS database username.

#. On the **Connection Properties** page, enter related parameters and select **Encrypt connection** to enable SSL encryption. (By default, **Encrypt connection** is not selected. You need to select it manually.)


   .. figure:: /_static/images/en-us_image_0000001145051614.jpg
      :alt: **Figure 3** Connection properties

      **Figure 3** Connection properties

#. Click **Connect** to connect to the DB instance.

   .. note::

      If the connection fails, ensure that preparations have been correctly made in :ref:`Preparations <rds_03_0007__section367520762117>` and try again.

.. |image1| image:: /_static/images/en-us_image_0000001191211453.png
