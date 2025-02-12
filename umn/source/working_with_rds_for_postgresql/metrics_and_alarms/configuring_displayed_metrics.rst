:original_name: rds_pg_06_0001.html

.. _rds_pg_06_0001:

Configuring Displayed Metrics
=============================

The RDS Agent monitors RDS DB instances and collects monitoring metrics only.

Description
-----------

This section describes the metrics that can be monitored by Cloud Eye as well as their namespaces and dimensions. You can use APIs provided by Cloud Eye to query the monitoring metrics and alarms generated for RDS.

Namespace
---------

SYS.RDS

DB Instance Monitoring Metrics
------------------------------

-  :ref:`Table 1 <rds_pg_06_0001__table3571040152710>` lists the performance metrics of PostgreSQL databases.

   .. _rds_pg_06_0001__table3571040152710:

   .. table:: **Table 1** Database performance metrics

      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | Metric                              | Name                         | Description                                                                  | Value Range   | Monitored Object                             | Monitoring Interval (Raw Data) |
      +=====================================+==============================+==============================================================================+===============+==============================================+================================+
      | rds001_cpu_util                     | CPU Usage                    | CPU usage of the monitored object                                            | 0-100%        | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds002_mem_util                     | Memory Usage                 | Memory usage of the monitored object                                         | 0-100%        | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds003_iops                         | IOPS                         | Average number of I/O requests processed by the system in a specified period | >= 0 counts/s | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds004_bytes_in                     | Network Input Throughput     | Incoming traffic in bytes per second                                         | >= 0 bytes/s  | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds005_bytes_out                    | Network Output Throughput    | Outgoing traffic in bytes per second                                         | >= 0 bytes/s  | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds039_disk_util                    | Storage Space Usage          | Storage space usage of the monitored object                                  | 0-100%        | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds040_transaction_logs_usage       | Transaction Logs Usage       | Storage space usage of transaction logs                                      | >= 0 MB       | Monitored object: database                   | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds041_replication_slot_usage       | Replication Slot Usage       | Storage space usage of replication slot files                                | >= 0 MB       | Monitored object: database                   | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds042_database_connections         | Database Connections in Use  | Number of database connections in use                                        | >= 0 counts   | Monitored object: database                   | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds043_maximum_used_transaction_ids | Maximum Used Transaction IDs | Maximum number of transaction IDs that have been used                        | >= 0 counts   | Monitored object: database                   | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds044_transaction_logs_generations | Transaction Logs Generation  | Size of transaction logs generated per second                                | >= 0 MB/s     | Monitored object: database                   | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds045_oldest_replication_slot_lag  | Oldest Replication Slot Lag  | Lagging size of the most lagging replica in terms of WAL data received       | >= 0 MB       | Monitored object: database                   | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds046_replication_lag              | Replication Lag              | Replication lag                                                              | >= 0 ms       | Monitored object: database                   | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds047_disk_total_size              | Total Storage Space          | Total storage space of the monitored object                                  | 40-4,000 GB   | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds048_disk_used_size               | Used Storage Space           | Used storage space of the monitored object                                   | 0-4,000 GB    | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds049_disk_read_throughput         | Disk Read Throughput         | Number of bytes read from the disk per second                                | >= 0 bytes/s  | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+
      | rds050_disk_write_throughput        | Disk Write Throughput        | Number of bytes written into the disk per second                             | >= 0 bytes/s  | Monitored object: ECS                        | 1 minute                       |
      |                                     |                              |                                                                              |               |                                              |                                |
      |                                     |                              |                                                                              |               | Monitored instance type: PostgreSQL instance |                                |
      +-------------------------------------+------------------------------+------------------------------------------------------------------------------+---------------+----------------------------------------------+--------------------------------+

Dimension
---------

===================== =========================
Key                   Value
===================== =========================
postgresql_cluster_id PostgreSQL DB instance ID
===================== =========================
