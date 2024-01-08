:original_name: rds_02_0016.html

.. _rds_02_0016:

Connecting to a DB Instance Through psql
========================================

You can use the PostgreSQL client psql to connect to a DB instance through a non-SSL connection or an SSL connection. The SSL connection is encrypted and therefore more secure.

Prerequisites
-------------

#. You have logged in to the ECS.

   -  To connect to a DB instance through an ECS, make sure that:

      -  The ECS and DB instance must be in the same VPC.
      -  The ECS must be allowed by the security group to access RDS DB instances.

         -  If the security group with which the target DB instance is associated is the default security group, you do not need to configure security group rules.

         -  If the security group with which the target DB instance is associated is not the default security group, check whether the security group rules allow the ECS to connect to the DB instance. For details, see :ref:`Configuring Security Group Rules <rds_02_0014>`.

            If the security group rules allow the access from the ECS, the ECS can connect to the DB instance.

            If the security group rules do not allow the access from the ECS, you need to add a security group rule. The ECS must be allowed by the security group to access DB instances.

#. You have installed a database client to connect to DB instances.

   For details, see :ref:`How Can I Install the PostgreSQL Client? <rds_faq_0029>`

Non-SSL Connection
------------------

#. Log in to the ECS or the device that can access RDS.

#. Run the following command to connect to the DB instance:

   **psql --no-readline -U** <*user*> **-h** <*host*> **-p** <*port*> **-d** <*datastore*> **-W**

   .. table:: **Table 1** Parameter description

      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter     | Description                                                                                                                                                                                                                                                                                      |
      +===============+==================================================================================================================================================================================================================================================================================================+
      | <*user*>      | Indicates the username of the RDS database account. The default administrator is **root**.                                                                                                                                                                                                       |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*host*>      | Indicates the IP address of the primary DB instance. To obtain this parameter, go to the **Basic Information** page of the DB instance. If the DB instance is accessed through the ECS, the IP address can be found in the **Floating IP Address** field in the **Connection Information** area. |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*port*>      | Indicates the database port in use. The default value is **5432**. To obtain this parameter, go to the **Basic Information** page of the DB instance. The port number can be found in the **Database Port** field in the **Connection Information** area.                                        |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | <*datastore*> | Indicates the name of the database (the default database name is **postgres**).                                                                                                                                                                                                                  |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   The parameter **-W** indicates that a password must be entered for the connection. After running this command, you will be prompted to enter a password.

   Example:

   Run the following command as user **root** to connect to a DB instance:

   **psql --no-readline -U root -h 192.168.0.44 -p 5432 -d postgres -W**

SSL Connection
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance. In the **DB Information** area on the **Basic Information** page, click |image2| in the **SSL** field to download the root certificate or certificate bundle.

#. Upload the root certificate to the ECS or save it to the device to be connected to the DB instance.

   For details about how to import the root certificate to the Linux OS on the ECS, see :ref:`How Can I Import the Root Certificate to a Windows or Linux OS? <rds_faq_0052>`

#. Connect to an RDS DB instance. The Linux OS is used as an example.

   **psql --no-readline -h** *<host>* **-p** *<port>* **"dbname=**\ *<database>* **user=**\ *<user>* **sslmode=verify-ca sslrootcert=**\ *<ca-file-directory>*\ **"**

   .. table:: **Table 2** Parameter description

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                        |
      +=======================+====================================================================================================================================================================================================================================================================================+
      | *<host>*              | IP address of the primary DB instance. To obtain this parameter, go to the **Basic Information** page of the DB instance. If the DB instance is accessed through the ECS, the IP address can be found in the **Floating IP Address** field in the **Connection Information** area. |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<port>*              | Database port in use. The default value is **5432**. To obtain this parameter, go to the **Basic Information** page of the DB instance. The port number can be found in the **Database Port** field in the **Connection Information** area.                                        |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<database>*          | Name of the database (the default database name is **postgres**).                                                                                                                                                                                                                  |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<user>*              | Username of the RDS database account. The default administrator is **root**.                                                                                                                                                                                                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<ca-file-directory>* | Directory of the CA certificate for the SSL connection. The certificate should be stored in the directory where the command is executed.                                                                                                                                           |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | sslmode               | SSL connection mode. Set it to **verify-ca** to use a CA to check whether the service is trusted.                                                                                                                                                                                  |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   Enter the password of the database account if the following information is displayed:

   Password:

   For example, to connect to a DB instance through an SSL connection as user **root**, run the following command:

   **psql --no-readline -h 192.168.0.44 -p 5432 "dbname=postgres user=root sslmode=verify-ca sslrootcert=/root/ca.pem"**

   **Password:**

#. The SSL connection is established if information similar to the following is displayed after you log in to the database:

   .. code-block::

      SSL connection (protocol: TLSv1.2, cipher: ECDHE-RSA-AES256-GCM-SHA384, bits: 256, compression: off)

.. |image1| image:: /_static/images/en-us_image_0000001744574182.png
.. |image2| image:: /_static/images/en-us_image_0000001791613293.png
