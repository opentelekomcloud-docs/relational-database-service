:original_name: rds_faq_0056.html

.. _rds_faq_0056:

How Can I Prevent Untrusted Source IP Addresses from Accessing RDS?
===================================================================

-  If you enable public accessibility, your EIP DNS and database port may be vulnerable to hacking. To protect information such as your EIP, DNS, database port, database account, and password, you are advised to set the range of source IP addresses in the RDS security group to ensure that only trusted source IP addresses can access your DB instances.
-  To prevent your database password from being cracked, set a strong password and periodically change it.
-  RDS for SQL Server includes defense against brute force cracking. If malicious individuals have obtained your EIP DNS, database port, or database login information and attempt a brute force attack, your service connections may be delayed. In this case, you can restrict the source connections and change the database username and password to prevent further damage.

   .. note::

      RDS for MySQL and RDS for PostgreSQL do not include defense against brute force attacks.

      For RDS for Microsoft SQL Server, defense against brute force attacks is enabled by default and cannot be disabled.
