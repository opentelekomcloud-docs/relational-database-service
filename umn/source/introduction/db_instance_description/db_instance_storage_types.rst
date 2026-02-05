:original_name: rds_01_0020.html

.. _rds_01_0020:

DB Instance Storage Types
=========================

The database system is generally an important part of an IT system and has high requirements on storage I/O performance. You can select a storage type based on service demands. You cannot change the storage type after the DB instance is created.

Description
-----------

RDS supports **Cloud SSD and** **Extreme SSD** to suit different performance requirements of your workloads.

-  Cloud SSD

   Stores data in cloud disks for decoupled storage and compute. The maximum throughput is 350 MB/s.

-  Extreme SSD

   Uses 25GE network and RDMA technologies to provide you with up to 1,000 MB/s throughput per disk and sub-millisecond latency.

Performance Comparison
----------------------

.. table:: **Table 1** Performance comparison

   +-----------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Item                  | Cloud SSD                                                      | Extreme SSD                                                                                                                     |
   +=======================+================================================================+=================================================================================================================================+
   | I/O performance       | Subpar I/O performance due to additional network I/O overheads | Higher I/O performance than cloud SSDs                                                                                          |
   +-----------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Elastic scalability   | Scaling in seconds                                             | Scaling in seconds                                                                                                              |
   +-----------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Maximum IOPS          | 50,000                                                         | 128,000                                                                                                                         |
   +-----------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Maximum throughput    | 350 MiB/s                                                      | For specifications with more than 32 vCPUs, the maximum throughput is 1,000 MiB/s.                                              |
   |                       |                                                                |                                                                                                                                 |
   |                       |                                                                | For specifications with 32 vCPUs or fewer, the maximum throughput may not reach 1,000 MiB/s due to the underlying architecture. |
   +-----------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Read/write latency    | Medium                                                         | Medium                                                                                                                          |
   +-----------------------+----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
