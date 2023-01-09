:original_name: rds_faq_0019.html

.. _rds_faq_0019:

What Do I Do If the Number of RDS Database Connections Reaches the Upper Limit?
===============================================================================

The number of database connections indicates the number of applications that can be simultaneously connected to a database, and is irrelevant to the maximum number of users allowed by your applications or websites.

If there is an excessive number of database connections, applications may fail to be connected, and the full and incremental backups may fail, affecting services.

Fault Locating
--------------

#. Check whether applications are connected, optimize the connections, and release unnecessary connections.
#. Check the specifications and scale them up if needed.
#. Check whether any metrics are abnormal and whether any alarms are generated on the Cloud Eye console. Cloud Eye monitors database metrics, such as the CPU usage, memory usage, storage space usage, and database connections, and allows you to set alarm policies to identify risks in advance if any alarms are generated. For details, see the *Cloud Eye User Guide*.
