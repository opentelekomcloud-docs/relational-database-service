:original_name: rds_02_0047.html

.. _rds_02_0047:

Connecting to a DB Instance Through a Private Network
=====================================================

You can connect to a DB instance through a non-SSL connection or an SSL connection. The SSL connection encrypts data and is more secure.

Prerequisites
-------------

#. You have logged in to an ECS.

   -  To connect to a DB instance through an ECS, you must ensure that:

      -  The ECS and DB instance must be in the same VPC.
      -  The ECS must be allowed by the security group to access the DB instance.

         -  If the security group with which the target DB instance is associated is the default security group, you do not need to configure security group rules.

         -  If the security group with which the target DB instance is associated is not the default security group, check whether the security group rules allow the ECS to connect to the DB instance. For details, see section :ref:`Configuring Security Group Rules <rds_02_0004>`.

            If the security group rules allow the access from the ECS, the ECS can connect to the DB instance.

            If the security group rules do not allow the access from the ECS, you need to add a security group rule. The ECS must be allowed by the security group to access the DB instance.

#. You have installed a database client to connect to DB instances.

   You can use a database client to connect to the target DB instance in the Linux or Windows OS.

   -  In the Linux OS, install the MySQL client on the device that can access RDS. It is recommended that you download a MySQL client running a version later than that of the DB instance.

      For details about how to obtain and install the MySQL client, see section :ref:`How Can I Install the MySQL Client? <rds_faq_0027>`

   -  In the Windows OS, you can use any common database client to connect to the target DB instance in a similar way.

      The database client MySQL-Front is used as an example in :ref:`Using MySQL-Front to Connect to a DB Instance <rds_02_0047__section103301531245>`.

.. _rds_02_0047__section103301531245:

Using MySQL-Front to Connect to a DB Instance
---------------------------------------------

#. Start MySQL-Front.

#. In the displayed dialog box, click **New**.


   .. figure:: /_static/images/en-us_image_0000001145211482.png
      :alt: **Figure 1** Connection management

      **Figure 1** Connection management

#. .. _rds_02_0047__li194201396457:

   Enter the information of the DB instance to be connected and click **Ok**, as shown in :ref:`Figure 2 <rds_02_0047__fig4664143131112>`.

   .. _rds_02_0047__fig4664143131112:

   .. figure:: /_static/images/en-us_image_0000001191131361.png
      :alt: **Figure 2** Adding an account

      **Figure 2** Adding an account

   .. table:: **Table 1** Parameter description

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                     |
      +===================================+=================================================================================================================================================================+
      | Name                              | Indicates the name of the database connection task. If you do not set this parameter, it will be the same as the **Host** value by default.                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Host                              | Indicates the floating IP address of the DB instance to be connected. To view the floating IP address and port of the DB instance, perform the following steps: |
      |                                   |                                                                                                                                                                 |
      |                                   | a. Log in to the RDS console.                                                                                                                                   |
      |                                   | b. Select the region in which the DB instance is located.                                                                                                       |
      |                                   | c. Click the target DB instance to enter the **Basic Information** page.                                                                                        |
      |                                   | d. In the **Connection Information** area, view the floating IP address.                                                                                        |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Port                              | Indicates the private network port of the DB instance.                                                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | User                              | Indicates the name of the user who will access the DB instance. The default user is **root**.                                                                   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Password                          | Indicates the password of the RDS database account.                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the displayed window, select the connection that you have created in :ref:`3 <rds_02_0047__li194201396457>` and click **Open**. If the connection information is correct, the DB instance is successfully connected.


   .. figure:: /_static/images/en-us_image_0000001191131363.png
      :alt: **Figure 3** Opening a session

      **Figure 3** Opening a session

   .. note::

      If the connection fails, see :ref:`What Should I Do If an ECS Cannot Connect to an RDS DB Instance Through a Private Network? <rds_faq_0020>`

SSL Connection
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance. In the **DB Information** area on the **Basic Information** page, click |image2| in the **SSL** field to download the root certificate or certificate bundle.

#. Import the root certificate to the Linux OS on the ECS. For details, see :ref:`How Can I Import the Root Certificate to a Windows or Linux OS? <rds_faq_0052>`

   .. note::

      -  Since April 2017, RDS has offered a new root certificate that has a 20-year validation period. The new certificate takes effect after DB instances are rebooted. Replace the old certificate before it expires to improve system security.

         For details, see section :ref:`How Can I Identify the Validity Period of an SSL Root Certificate? <rds_faq_0051>`

      -  You can also download the certificate bundle, which contains both the new certificate provided since April 2017 and the old certificate.

#. Connect to the RDS DB instance. The Linux OS is used as an example.

   **mysql -h** <*host*> **-P** *<port>* **-u** <*userName*> **-p** **--ssl-ca=**\ <*caDIR*>

   .. table:: **Table 2** Parameter description

      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter    | Description                                                                                                                                                                                            |
      +==============+========================================================================================================================================================================================================+
      | <*host*>     | Floating IP address. To obtain this parameter, go to the **Basic Information** page of the DB instance and view the floating IP address in the **Connection Information** area.                        |
      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<port>*     | Database port. By default, the value is **3306**. To obtain this parameter, go to the **Basic Information** page of the DB instance and view the database port in the **Connection Information** area. |
      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*userName*> | Username of the RDS database account. The default administrator is **root**.                                                                                                                           |
      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*caDIR*>    | Directory of the CA certificate. The certificate should be stored in the directory where the command is executed.                                                                                      |
      +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   For example, to connect to a DB instance through an SSL connection as user **root**, run the following command:

   **mysql -h 172.16.0.31 -P 3306 -u root -p --ssl-ca=ca.pem**

   Enter the password of the database account if the following information is displayed:

   .. code-block::

      Enter password:

   .. note::

      If the connection fails, see :ref:`What Should I Do If an ECS Cannot Connect to an RDS DB Instance Through a Private Network? <rds_faq_0020>`

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191131359.png
