:original_name: rds_sqlserver_06_0001.html

.. _rds_sqlserver_06_0001:

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

-  :ref:`Table 1 <rds_sqlserver_06_0001__en-us_topic_0171122394_table2501556415126>` lists details about ECS metrics.

   .. _rds_sqlserver_06_0001__en-us_topic_0171122394_table2501556415126:

   .. table:: **Table 1** ECS performance metrics

      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | Metric ID                    | Name                        | Description                                                                  | Value Range   | Monitored Object                                       | Monitoring Interval (Raw Data) |
      +==============================+=============================+==============================================================================+===============+========================================================+================================+
      | rds001_cpu_util              | CPU Usage                   | CPU usage of the monitored object                                            | 0%-100%       | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds003_iops                  | IOPS                        | Average number of I/O requests processed by the system in a specified period | >= 0 counts/s | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds039_disk_util             | Storage Space Usage         | Storage space usage of the monitored object                                  | 0%-100%       | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds002_mem_util              | Memory Usage                | Memory usage of the monitored object                                         | 0%-100%       | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds004_bytes_in              | Network Input Throughput    | Incoming traffic in bytes per second                                         | >= 0 bytes/s  | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds005_bytes_out             | Network Output Throughput   | Outgoing traffic in bytes per second                                         | >= 0 bytes/s  | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds049_disk_read_throughput  | Disk Read Throughput        | Number of bytes read from the disk per second                                | >= 0 bytes/s  | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds050_disk_write_throughput | Disk Write Throughput       | Number of bytes written into the disk per second                             | >= 0 bytes/s  | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds047_disk_total_size       | Total Storage Space         | Total storage space of the monitored object                                  | 40-4,000 GB   | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds048_disk_used_size        | Used Storage Space          | Used storage space of the monitored object                                   | 0-4,000 GB    | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds053_avg_disk_queue_length | Average Disk Queue Length   | Number of processes to be written into the monitored object                  | >= 0          | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds054_db_connections_in_use | Database Connections in Use | Number of database connections in use                                        | >=0 counts    | Monitored object: database                             | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+

-  :ref:`Table 2 <rds_sqlserver_06_0001__table757413467462>` lists the performance metrics of Microsoft SQL Server databases.

   .. _rds_sqlserver_06_0001__table757413467462:

   .. table:: **Table 2** Database performance metrics

      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | Metric ID                    | Name                        | Description                                                                  | Value Range   | Monitored Object                                       | Monitoring Interval (Raw Data) |
      +==============================+=============================+==============================================================================+===============+========================================================+================================+
      | rds001_cpu_util              | CPU Usage                   | CPU usage of the monitored object                                            | 0-100%        | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds002_mem_util              | Memory Usage                | Memory usage of the monitored object                                         | 0-1           | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds003_iops                  | IOPS                        | Average number of I/O requests processed by the system in a specified period | >= 0 counts/s | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds004_bytes_in              | Network Input Throughput    | Incoming traffic in bytes per second                                         | >= 0 bytes/s  | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds005_bytes_out             | Network Output Throughput   | Outgoing traffic in bytes per second                                         | >= 0 bytes/s  | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds039_disk_util             | Storage Space Usage         | Storage space usage of the monitored object                                  | 0-1           | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds047_disk_total_size       | Total Storage Space         | Total storage space of the monitored object                                  | 40-4,000 GB   | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds048_disk_used_size        | Used Storage Space          | Used storage space of the monitored object                                   | 0-4,000 GB    | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds049_disk_read_throughput  | Disk Read Throughput        | Number of bytes read from the disk per second                                | >= 0 bytes/s  | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds050_disk_write_throughput | Disk Write Throughput       | Number of bytes written into the disk per second                             | >= 0 bytes/s  | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds053_avg_disk_queue_length | Average Disk Queue Length   | Number of processes to be written into the monitored object                  | >= 0          | Monitored object: ECS                                  | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+
      | rds054_db_connections_in_use | Database Connections in Use | Number of database connections in use                                        | >= 0 counts   | Monitored object: database                             | 1 minute                       |
      |                              |                             |                                                                              |               |                                                        |                                |
      |                              |                             |                                                                              |               | Monitored instance type: Microsoft SQL Server instance |                                |
      +------------------------------+-----------------------------+------------------------------------------------------------------------------+---------------+--------------------------------------------------------+--------------------------------+

Dimension
---------

========================= ========================================
Key                       Value
========================= ========================================
rds_instance_sqlserver_id Microsoft SQL Server DB instance node ID
========================= ========================================
