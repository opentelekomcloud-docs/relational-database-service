:original_name: rds_faq_0055.html

.. _rds_faq_0055:

What Is the Maximum Number of Connections to an RDS DB Instance?
================================================================

RDS does not have constraints on the number of connections. This number is determined by the default value and value range of the DB engine. For example, you can set **max_connections** and **max_user_connections** in a parameter template to configure the maximum number of connections for an RDS for MySQL DB instance.

Changing the Maximum Number of Connections
------------------------------------------

.

You can change the maximum number of connections using commands.

#. Query the maximum number of connections.

   **show global variables like 'max_connections';**

#. Change the value of **max_connections** under **mysqld** in the **my.cnf** file.

   **[mysqld]**

   **max_connections = 1000**

Setting the Maximum Number of RDS for MySQL Connections to an Appropriate Value
-------------------------------------------------------------------------------

-  In addition to the value of **max_connections**, the maximum number of concurrent client connections allowed by MySQL is also limited by the maximum number of files that can be opened by a single process in the operating system. For example, if the maximum number of files that can be opened by each process is set to **100** in the operating system, the **max_connections** parameter does not take effect even if it is set to **200**.

   Check the maximum number of files that can be opened by a single process in the operating system. The default value is **1024**.

   **ulimit -n**

   The parameter **open_files_limit** indicates the maximum number of files that can be opened by a single process, which is read from the operating system during MySQL startup.

   Check the value of **open_files_limit**.

   **show variables like 'open_files_limit';**

-  Suggestions

   The maximum number of MySQL connections can be customized provided that it is allowed by your instance specifications. The maximum number of connections is closely related to the instance memory. For details, see :ref:`About max_connections <rds_faq_0055__section164061146172516>`.

   In actual scenarios, set the maximum number of connections to an appropriate value because more connections lead to large resource consumption.

.. _rds_faq_0055__section164061146172516:

About max_connections
---------------------

**max_connections**: maximum number of clients that can be connected at the same time. If this parameter is set to **default**, it is related to the memory (unit: GB) of the DB instance. The calculation formula is as follows:

**Estimated value of max_connections = Available node memory/Estimated memory occupied by a single connection**

.. note::

   -  Available node memory = Total memory - Memory occupied by the buffer pool - 1 GB (mysqld process/OS/monitoring program)
   -  Estimated memory usage of a single connection (single_thread_memory) = thread_stack (256 KB) + binlog_cache_size (32 KB) + join_buffer_size (256 KB) + sort_buffer_size (256 KB) + read_buffer_size (128 KB) + read_rnd_buffer_size (256 KB) ≈ 1 MB

The following table lists the default values of **max_connections** for different memory specifications.

.. table:: **Table 1** Max_connections for different memory specifications

   =========== ===========
   Memory (GB) Connections
   =========== ===========
   512         100,000
   384         80,000
   256         60,000
   128         30,000
   64          18,000
   32          10,000
   16          5,000
   8           2,500
   4           1,500
   2           800
   =========== ===========
