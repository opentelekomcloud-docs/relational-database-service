:original_name: rds_pg_11_0011.html

.. _rds_pg_11_0011:

Security Best Practices
=======================

PostgreSQL has earned a reputation for reliability, stability, and data consistency, and has become the preferred choice as an open-source relational database for many enterprises. RDS for PostgreSQL is a cloud-based web service that is reliable, scalable, easy to manage, and immediately ready for use.

Make security configurations from the following dimensions to meet your service needs.

-  :ref:`Configuring the Maximum Number of Connections to the Database <rds_pg_11_0011__section191901740105814>`
-  :ref:`Configuring the Timeout for Client Authentication <rds_pg_11_0011__section17110125465819>`
-  :ref:`Configuring SSL and Encryption Algorithm <rds_pg_11_0011__section419316113594>`
-  :ref:`Configuring Password Encryption <rds_pg_11_0011__section1244942714596>`
-  :ref:`Disabling the Backslash Quote <rds_pg_11_0011__section17384134317596>`
-  :ref:`Periodically Checking and Deleting Roles That Are No Longer Used <rds_pg_11_0011__section11632185016594>`
-  :ref:`Revoking All Permissions on the public Schema <rds_pg_11_0011__section1547261618018>`
-  :ref:`Setting a Proper Password Validity Period for a User Role <rds_pg_11_0011__section19367142416014>`
-  :ref:`Configuring the Log Level to Record SQL Statements That Cause Errors <rds_pg_11_0011__section104480459018>`
-  :ref:`Enabling Data Backup <rds_pg_11_0011__section1319417131615>`
-  :ref:`Avoiding Binding an EIP to Your RDS for PostgreSQL Instance <rds_pg_11_0011__section733814410110>`
-  :ref:`Configuring the Delay for Account Authentication Failures <rds_pg_11_0011__section183391014201212>`

.. _rds_pg_11_0011__section191901740105814:

Configuring the Maximum Number of Connections to the Database
-------------------------------------------------------------

The **max_connections** parameter specifies the maximum concurrent connections allowed in a database. If the value of this parameter is large, the RDS for PostgreSQL database may request more System V shared memory or semaphore. As a result, the requested shared memory or semaphore may exceed the default value on the OS. Set **max_connections** based on service complexity. For details, see :ref:`Suggestions on PostgreSQL Parameter Tuning <rds_pg_10_0001>`.

.. _rds_pg_11_0011__section17110125465819:

Configuring the Timeout for Client Authentication
-------------------------------------------------

The **authentication_timeout** parameter specifies the maximum duration allowed to complete client authentication, in seconds. This parameter prevents clients from occupying a connection for a long time. The default value is 60s. If client authentication is not complete within the specified period, the connection is forcibly closed. Using this parameter can enhance the security of your RDS for PostgreSQL instance.

.. _rds_pg_11_0011__section419316113594:

Configuring SSL and Encryption Algorithm
----------------------------------------

SSL is recommended for TCP/IP connections because SSL ensures that all communications between clients and servers are encrypted, preventing data leakage and tampering and ensuring data integrity. When configuring SSL, configure the TLS protocol and encryption algorithm on the server. TLSv1.2 and EECDH+ECDSA+AESGCM:EECDH+aRSA+AESGCM:EDH+aRSA+AESGCM:EDH+aDSS+AESGCM:!aNULL:!eNULL:!LOW:!3DES:!MD5:!EXP:!SRP:!RC4 are recommended. For details, see :ref:`SSL Connection <rds_02_0016>`.

To configure the TLS protocol and encryption algorithm, use the parameters **ssl_min_protocol_version** and **ssl_ciphers**.

.. _rds_pg_11_0011__section1244942714596:

Configuring Password Encryption
-------------------------------

Passwords must be encrypted. When you use **CREATE USER** or **ALTER ROLE** to change a password, the password is stored in a system catalog after being encrypted by default. **scram-sha-256** is recommended for password encryption. To change the password encryption algorithm, change the value of **password_encryption**.

The **MD5** option is used only for compatibility with earlier versions. New DB instances use **scram-sha-256** by default.

.. important::

   The modification of **password_encryption** takes effect only after the password is reset.

.. _rds_pg_11_0011__section17384134317596:

Disabling the Backslash Quote
-----------------------------

The **backslash_quote** parameter specifies whether a single quotation mark (') in a string can be replaced by a backslash quote (\\'). The preferred, SQL-standard way to represent a single quotation mark is by doubling it (''). If client-side code does escaping incorrectly then an SQL-injection attack is possible. You are advised to set **backslash_quote** to **safe_encoding** to reject queries in which a single quotation mark appears to be escaped by a backslash, preventing SQL injection risks.

.. _rds_pg_11_0011__section11632185016594:

Periodically Checking and Deleting Roles That Are No Longer Used
----------------------------------------------------------------

Check whether all roles are mandatory. Every unknown role must be reviewed to ensure that it is used properly. If any role is no longer used, delete it. To query roles, run the following command:

**SELECT rolname FROM pg_roles;**

.. _rds_pg_11_0011__section1547261618018:

Revoking All Permissions on the public Schema
---------------------------------------------

The **public** schema is the default schema. All users can access objects in it, including tables, functions, and views, which may cause security vulnerabilities. You can run the following command as user **root** to revoke the permissions:

**revoke all on schema public from public;**

.. _rds_pg_11_0011__section19367142416014:

Setting a Proper Password Validity Period for a User Role
---------------------------------------------------------

When creating a role, you can use the VALID UNTIL keyword to specify when the password of the role becomes invalid. If this keyword is ignored, the password will be valid permanently. You are advised to change the password periodically, for example, every three months. To configure a password validity period, run the following command:

**CREATE ROLE name WITH PASSWORD** *'password'* **VALID UNTIL 'timestamp';**

To check whether a password validity period is configured, run the following command:

**SELECT rolname,rolvaliduntil FROM pg\\_roles WHERE rolsuper = false AND rolvaliduntil IS NULL;**

.. _rds_pg_11_0011__section104480459018:

Configuring the Log Level to Record SQL Statements That Cause Errors
--------------------------------------------------------------------

The **log_min_error_statement** parameter specifies which SQL statements that cause errors can be recorded in server logs. The SQL statements of the specified level or higher are recorded in logs. Valid values include **debug5**, **debug4**, **debug3**, **debug2**, **debug1**, **info**, **notice**, **warning**, **error**, **log**, **fatal**, and **panic**. The value of **log_min_error_statement** must be at least **error**.

.. _rds_pg_11_0011__section1319417131615:

Enabling Data Backup
--------------------

When you create an RDS DB instance, an automated backup policy is enabled by default with the retention period set to seven days. You can change the backup retention period as required. RDS for PostgreSQL DB instances support automated backups and manual backups. You can periodically back up your instance. If the instance fails or data is damaged, restore it using backups to ensure data reliability. For details, see Data Backups.

.. _rds_pg_11_0011__section733814410110:

Avoiding Binding an EIP to Your RDS for PostgreSQL Instance
-----------------------------------------------------------

Do not deploy your instance on the Internet or in a demilitarized zone (DMZ). Instead, deploy it on a private network and use routers or firewalls to control access to your instance. Do not bind an EIP to your instance to prohibit unauthorized access and DDoS attacks from the Internet. If you have bound an EIP to your instance, you are advised to unbind it. If you do need an EIP, configure security group rules to restrict the source IP addresses that can access your instance.

.. _rds_pg_11_0011__section183391014201212:

Configuring the Delay for Account Authentication Failures
---------------------------------------------------------

By default, RDS for PostgreSQL instances have a built-in auth_delay extension. auth_delay causes the server to stop for a short period of time before an authentication failure message is returned, making it more difficult to crack the database password. To configure the delay for account authentication failures, change the value of the **auth_delay.milliseconds** parameter (which indicates the number of milliseconds to wait before reporting an authentication failure) by referring to Modifying Parameters of an RDS for PostgreSQL Instance. The default value of this parameter is **0**.
