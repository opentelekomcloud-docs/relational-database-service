:original_name: rds_pg_11_0029.html

.. _rds_pg_11_0029:

Configuring SSL Encryption
==========================

SSL is enabled by default when you create an RDS for PostgreSQL DB instance and cannot be disabled after the instance is created. SSL encryption ensures that all communications between a client and server are encrypted, preventing data leakage and tampering and ensuring data integrity.

Impact of SSL Encryption on Database Performance
------------------------------------------------

Enabling SSL reduces the read-only and read/write performance of your instance by about 20%.

The impact varies depending on the service model. SSL encryption has little impact on database performance if there are complex SQL statements being executed because the execution of such statements takes much time. But SSL encryption will decrease the performance if simple SQL statements are being executed because the execution is fast.

Checking Whether SSL Is Enabled on the Server
---------------------------------------------

By default, SSL is enabled on the RDS for PostgreSQL instance server. You can log in to the instance and run the following SQL command to check whether SSL is enabled:

.. code-block::

   show ssl;

-  If the **ssl** value is **on**, SSL is enabled on the server.
-  If the **ssl** value is **off**, SSL is disabled on the server.

.. note::

   SSL is enabled on the server by default and cannot be disabled.

Checking Whether SSL Is Enabled on the Client
---------------------------------------------

You can check whether the client uses SSL encryption in either of the following ways:

-  Check whether the following information is displayed when you use psql to connect to the DB instance:

   .. code-block::

      SSL connection (protocol: TLSv1.2, cipher: ECDHE-RSA-AES256-GCM-SHA384, bits: 256, compression: off)

   -  **protocol** indicates the SSL connection protocol, which is **TLSv1.2**.
   -  **cipher** indicates the encryption algorithm used for SSL connection, which is **ECDHE-RSA-AES256-GCM-SHA384**.
   -  **bits** indicates the key length, which is **256** bits.

-  Query the **pg_stat_ssl** view to check whether the client uses SSL connection. If yes, corresponding connection information is displayed in the view.

   .. code-block::

      SELECT * FROM pg_stat_ssl;

   This query returns the statistics of all current SSL connections, including the process ID, client IP address, SSL protocol version, SSL encryption algorithm, and validity and expiration date of the client certificate. If the client uses SSL connection, you can view the related information in this view.

Parameters Related to SSL Encryption on the Server
--------------------------------------------------

.. table:: **Table 1** Parameters related to SSL encryption on the server

   +--------------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Value                                         | Description                                                                                                                                                                                                                                |
   +==========================+===============================================+============================================================================================================================================================================================================================================+
   | ssl                      | on                                            | SSL is enabled by default and **cannot be disabled**.                                                                                                                                                                                      |
   +--------------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ssl_cert_file            | /CA/server.pem                                | Location of the SSL certificate file on the server, **which cannot be changed**.                                                                                                                                                           |
   +--------------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ssl_ciphers              | ALL:!ADH:!LOW:!EXP:!MD5:!3DES:!DES:@STRENGTH; | SSL cipher list for secure connection. You can change the value based on security requirements. Recommended cipher list: EECDH+ECDSA+AESGCM:EECDH+aRSA+AESGCM:EDH+aRSA+AESGCM:EDH+aDSS+AESGCM:!aNULL:!eNULL:!LOW:!3DES:!MD5:!EXP:!SRP:!RC4 |
   +--------------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ssl_key_file             | /CA/server.key                                | Location of the SSL private key file on the server, **which cannot be changed**.                                                                                                                                                           |
   +--------------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ssl_min_protocol_version | TLSv1.2                                       | Minimum SSL/TLS protocol version to be used. You can change the value based on security requirements. TLSv1.2 or later is recommended.                                                                                                     |
   +--------------------------+-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Parameters Related to SSL Encryption on the Client
--------------------------------------------------

After SSL is enabled for an RDS for PostgreSQL instance, the client can connect to the instance through SSL.

When the client connects to the instance, you can set **sslmode** based on the site requirements.

-  If SSL connection is used, **sslmode** can be set to **allow**, **prefer**, **Require**, **Verify-CA**, or **Verify-Full**. The default value is **prefer**.
-  If SSL connection is not used, set **sslmode** to **Disable**.

.. note::

   If **sslmode** is set to **Verify-CA** or **Verify-Full**, you need to set the **Root certificate** parameter, which indicates the path of the database CA certificate. The CA certificate can be downloaded from the console.

.. table:: **Table 2** sslmode values

   +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Value       | Description                                                                                                                                                                                                                             |
   +=============+=========================================================================================================================================================================================================================================+
   | disable     | The client does not use the SSL connection.                                                                                                                                                                                             |
   +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | allow       | The client attempts to establish an SSL or TLS connection. If the server does not support the SSL or TLS connection, the client connects to the server in common text mode.                                                             |
   +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | prefer      | Default value. The client attempts to establish an SSL connection first. If the server does not support the SSL connection, the client connects to the server in common text mode.                                                      |
   +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | require     | The client only attempts to establish an SSL connection, encrypts the data link, and does not verify the validity of the server certificate.                                                                                            |
   +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | verify-ca   | The client uses SSL to connect to the server and verifies the validity of the server certificate.                                                                                                                                       |
   +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | verify-full | The client uses SSL to connect to the server, verifies the validity of the server certificate, and checks whether the CN or DNS in the certificate is consistent with the database connection address configured during the connection. |
   +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
