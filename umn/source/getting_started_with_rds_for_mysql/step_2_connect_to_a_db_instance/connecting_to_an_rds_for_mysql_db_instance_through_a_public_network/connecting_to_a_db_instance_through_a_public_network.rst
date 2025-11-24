:original_name: en-us_topic_connect_instance.html

.. _en-us_topic_connect_instance:

Connecting to a DB Instance Through a Public Network
====================================================

You can connect to a DB instance through a non-SSL connection or an SSL connection. The SSL connection encrypts data and is more secure.

.. _en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_section367520762117:

Prerequisites
-------------

#. An EIP has been bound to the target DB instance and security group rules have been configured.

   a. .. _en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_li1728416257345:

      Bind an EIP to the target DB instance.

      For details about how to bind an EIP, see section :ref:`Binding an EIP <rds_02_0025>`.

   b. .. _en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_li85977812411:

      Obtain the IP address of the local device.

   c. Configure security group rules.

      Add the IP address obtained in :ref:`1.b <en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_li85977812411>` and the instance port to the inbound rule of the security group.

      For details about how to configure a security group rule, see section :ref:`Configuring Security Group Rules <rds_02_0009>`.

   d. Run the **ping** command to check the connectivity between the local device and the EIP that has been bound to the DB instance in :ref:`1.a <en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_li1728416257345>`.

#. You have installed a database client to connect to DB instances.

   You can use a database client to connect to the target DB instance in the Linux or Windows operating system (OS).

   -  In the Linux OS, you need to install a MySQL client on the ECS. It is recommended that you download a MySQL client running a version later than that of the DB instance.

      For details about how to obtain and install the MySQL client, see section :ref:`How Can I Install the MySQL Client? <rds_faq_0027>`

   -  In the Windows OS, you can use any common database client to connect to the target DB instance in a similar way.

      The database client MySQL-Front is used as an example in :ref:`Using MySQL-Front to Connect to a DB Instance <en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_section8112152217539>`.

.. _en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_section8112152217539:

Using MySQL-Front to Connect to a DB Instance
---------------------------------------------

#. Start MySQL-Front.

#. In the displayed dialog box, click **New**.


   .. figure:: /_static/images/en-us_image_0000001191211477.png
      :alt: **Figure 1** Connection management

      **Figure 1** Connection management

#. Enter the information of the DB instance to be connected and click **Ok**, as shown in :ref:`Figure 2 <en-us_topic_connect_instance__en-us_topic_0154555358_fig4664143131112>`.

   .. _en-us_topic_connect_instance__en-us_topic_0154555358_fig4664143131112:

   .. figure:: /_static/images/en-us_image_0000001191131321.png
      :alt: **Figure 2** Adding an account

      **Figure 2** Adding an account

   .. table:: **Table 1** Parameter description

      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Description                                                                                                                                 |
      +===========+=============================================================================================================================================+
      | Name      | Indicates the name of the database connection task. If you do not set this parameter, it will be the same as the **Host** value by default. |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Host      | Indicates the EIP of the DB instance to be connected.                                                                                       |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Port      | Indicates the private network port of the DB instance.                                                                                      |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | User      | Indicates the name of the user who will access the DB instance. The default user is **root**.                                               |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Password  | Indicates the password of the RDS database account.                                                                                         |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+

#. In the displayed window, select the connection that you have created in :ref:`Figure 3 <en-us_topic_connect_instance__en-us_topic_0154555358_fig3870144665113>` and click **Open**.

   If the connection information is correct, the DB instance is successfully connected.

   .. _en-us_topic_connect_instance__en-us_topic_0154555358_fig3870144665113:

   .. figure:: /_static/images/en-us_image_0000001145051640.png
      :alt: **Figure 3** Opening a session

      **Figure 3** Opening a session

   .. note::

      If the connection fails, ensure that preparations have been correctly made in :ref:`Prerequisites <en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_section367520762117>` and try again.

Using SSL to Connect to a DB Instance
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance. In the **Basic Information** area on the **Overview** page, click **Download** in the **SSL** field to download the root certificate or certificate bundle.

#. Import the root certificate to the Linux OS on the ECS. For details, see :ref:`How Can I Import the Root Certificate to a Windows or Linux OS? <rds_faq_0052>`

   .. note::

      -  Since April 2017, RDS has offered a new root certificate that has a 20-year validation period. The new certificate takes effect after DB instances are rebooted. Replace the old certificate before it expires to improve system security.

         For details, see section :ref:`How Can I Identify the Validity Period of an SSL Root Certificate? <rds_faq_0051>`

      -  You can also download the certificate bundle, which contains both the new certificate provided since April 2017 and the old certificate.

#. Connect to an RDS DB instance. The Linux OS is used as an example.

   **mysql -h** <*host*> **-P** *<port>* **-u** <*userName*> **-p** **--ssl-ca=**\ <*caDIR*>

   .. table:: **Table 2** Parameter description

      +--------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Parameter    | Description                                                                                                                     |
      +==============+=================================================================================================================================+
      | <*host*>     | Indicates the EIP of the DB instance to be connected.                                                                           |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------+
      | *<port>*     | Indicates the port of the DB instance to be connected.                                                                          |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------+
      | <*userName*> | Indicates the username of the RDS database account. The default administrator is **root**.                                      |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------+
      | <*caDIR*>    | Indicates the directory of the CA certificate. The certificate should be stored in the directory where the command is executed. |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------+

   For example, to connect to a DB instance through an SSL connection as user **root**, run the following command:

   **mysql -h 172.16.0.31 -P 3306 -u root -p --ssl-ca=ca.pem**

   Enter the password of the database account if the following information is displayed:

   .. code-block::

      Enter password:

   .. note::

      If the connection fails, ensure that preparations have been correctly made in :ref:`Prerequisites <en-us_topic_connect_instance__en-us_topic_0154555358_en-us_topic_0153118658_section367520762117>` and try again.

.. |image1| image:: /_static/images/en-us_image_0000001145051824.png
