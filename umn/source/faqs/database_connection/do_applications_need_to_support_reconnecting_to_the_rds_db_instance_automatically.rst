:original_name: rds_faq_0024.html

.. _rds_faq_0024:

Do Applications Need to Support Reconnecting to the RDS DB Instance Automatically?
==================================================================================

It is recommended that your applications support automatic reconnections to the database. After a database reboot, your applications will automatically reconnect to the database to increase service availability and continuity.

To reduce resource consumption and improve performance, configure your applications to connect to the database using a persistent connection.
