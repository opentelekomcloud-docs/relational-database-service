:original_name: rds_faq_0011.html

.. _rds_faq_0011:

How Can I Identify Data Corruption?
===================================

-  Data tampering

   Lots of security measures are provided to ensure that only authenticated users have permissions to perform operations on database table records. Database tables can be accessed only through specific database ports.

   Verifying package during primary/standby synchronization can prevent data tampering. MySQL uses the InnoDB storage engine to prevent data from being damaged.

-  DB instance servers may be powered off suddenly, causing database page corruption and database rebooting failures.

   If a primary DB instance becomes faulty, RDS switches to the standby DB instance within 1 to 5 minutes to provide services for you. Databases cannot be accessed during a failover. You must configure automatic reconnection between your applications and RDS to make sure that your applications are available after the failover.
