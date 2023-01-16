:original_name: rds_faq_0001.html

.. _rds_faq_0001:

What Should I Pay Attention to When Using RDS?
==============================================

#. DB instance operating systems (OSs) are invisible to you. Your applications can access a database only through an IP address and a port.

#. The backup files stored in Object Storage Service (OBS) and the Elastic Cloud Server (ECS) used by RDS are invisible to you. They are visible only to the RDS instance management system.

#. Before viewing the DB instance list, ensure that the region is the same as the region where the DB instance is purchased.

#. Precautions after purchasing RDS:

   After purchasing RDS DB instances, you do not need to perform basic database O&M operations, such as applying HA and security patches. However, you must still pay attention to:

   a. Whether the CPU, input/output operations per second (IOPS), and space of the RDS DB instance are sufficient. If any of these becomes insufficient, change the CPU/Memory or scale up the DB instance.
   b. Whether the performance of the RDS DB instances is adequate, a large number of slow query SQL statements exist, SQL statements need to be optimized, or any indexes are redundant or missing.
