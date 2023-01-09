:original_name: rds_11_0012.html

.. _rds_11_0012:

Introducing Read Replicas
=========================

Introduction
------------

RDS for MySQL supports read replicas.

In read-intensive scenarios, a single DB instance may be unable to handle the read pressure and service performance may be affected. To expand the DB instance read ability to offload read pressure on the database, you can create read replicas in a region. These read replicas can process a large number of read requests and increase application throughput. You need to separately configure connection addresses for the primary DB instance and each read replica on your applications so that all read requests can be sent to read replicas and write requests to the primary DB instance.

A read replica uses a single-node architecture (without a slave node). Changes to the primary DB instance are also automatically synchronized to all associated read replicas through the native MySQL replication function. The synchronization is not affected by network latency. Read replicas and the primary DB instance must be in the same region but can be in different AZs.

Functions
---------

-  Read replica specifications can be different from primary DB instance specifications. It is recommended that the read replica specifications be greater than or equal to the primary DB instance specifications to prevent long delay and high load.

-  Read replicas support system performance monitoring.

   RDS provides up to 20 monitoring metrics, including storage space, IOPS, the number of database connections, CPU usage, and network traffic. You can view these metrics to learn about the load on DB instances.

-  Read replicas do not support automated backups or manual backups.

-  Read replicas do not support restoration from backups to new, existing, or original read replicas.

-  Data cannot be migrated to read replicas.

-  Read replicas do not support database creation and deletion.

-  Read replicas do not support database account creation.

Constraints
-----------

A maximum of five read replicas can be created for each primary DB instance.

Creating and Managing a Read Replica
------------------------------------

-  :ref:`Creating a Read Replica <en-us_topic_add_read_replica>`
-  :ref:`Managing a Read Replica <rds_11_0015>`
