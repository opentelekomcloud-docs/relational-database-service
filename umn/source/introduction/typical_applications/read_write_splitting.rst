:original_name: rds_01_0012.html

.. _rds_01_0012:

Read/Write Splitting
====================

RDS for MySQL, RDS for PostgreSQL, RDS for SQL Server 2019 Enterprise Edition, and 2017 Enterprise Edition DB instances support read replicas to offload read traffic from primary DB instances.

For RDS for MySQL and RDS for PostgreSQL, the primary DB instances and read replicas have independent connection addresses. A maximum of five read replicas can be created for each RDS for MySQL or RDS for PostgreSQL DB instance. For details about how to create a read replica, see :ref:`Creating a Read Replica (RDS for MySQL) <en-us_topic_add_read_replica>` and :ref:`Creating a Read Replica (RDS for PostgreSQL) <rds_add_read_replica_pg>`.

To offload read pressure on the primary DB instance, you can create one or more read replicas in the same region as the primary instance. These read replicas can process a large number of read requests and increase application throughput. You need to separately configure connection addresses for the primary DB instance and each read replica on your applications so that all read requests can be sent to read replicas and write requests to the primary DB instance.
