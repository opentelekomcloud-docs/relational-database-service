:original_name: rds_01_0020.html

.. _rds_01_0020:

DB Instance Storage Types
=========================

The database system is generally an important part of an IT system and has high requirements on storage I/O performance. You can select a storage type based on service demands. You cannot change the storage type after the DB instance is created.

Description
-----------

RDS supports **Cloud SSD,** **Extreme SSD** and **Flexible SSD** to suit different performance requirements of your workloads.

-  Cloud SSD

   Stores data in cloud disks for decoupled storage and compute. The maximum throughput is 350 MB/s.

-  Extreme SSD

   Uses 25GE network and RDMA technologies to provide you with up to 1,000 MB/s throughput per disk and sub-millisecond latency.

-  Flexible SSD

   Decouples capacity from performance and allows for tailored IOPS and throughput for your business requirements. This storage type is ideal for mainstream interactive applications that require high performance and low latency.

   You can preconfigure an IOPS ranging from 3,000 to 128,000. This IOPS must also be less than or equal to 500 times the storage capacity. You can preconfigure a throughput ranging from 125 to 1,000 MiB/s. This throughput must also be less than or equal to the IOPS divided by 4.

Performance Comparison
----------------------

.. table:: **Table 1** Performance comparison

   +---------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Item                | Cloud SSD                                                      | Extreme SSD                                                                                                                     | Flexible SSD                  |
   +=====================+================================================================+=================================================================================================================================+===============================+
   | I/O performance     | Subpar I/O performance due to additional network I/O overheads | Higher I/O performance than cloud SSDs                                                                                          | On-demand IOPS and throughput |
   +---------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Elastic scalability | Scaling in seconds                                             | Scaling in seconds                                                                                                              | Scaling in seconds            |
   +---------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Maximum IOPS        | 50,000                                                         | 128,000                                                                                                                         | 128,000                       |
   +---------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Maximum throughput  | 350 MiB/s                                                      | For specifications with more than 32 vCPUs, the maximum throughput is 1,000 MiB/s.                                              | 1,000 MiB/s                   |
   |                     |                                                                |                                                                                                                                 |                               |
   |                     |                                                                | For specifications with 32 vCPUs or fewer, the maximum throughput may not reach 1,000 MiB/s due to the underlying architecture. |                               |
   +---------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Read/write latency  | Medium                                                         | Medium                                                                                                                          | Medium                        |
   +---------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
