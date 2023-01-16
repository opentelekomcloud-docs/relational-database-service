:original_name: rds_08_00001.html

.. _rds_08_00001:

Suggestions on MySQL Parameter Tuning
=====================================

Parameters are key configuration items in a database system. Improper parameter settings may adversely affect the stable running of databases. This section describes some important parameters for your reference. For details, visit the `MySQL official website <http://dev.mysql.com/doc/refman/5.6/en/server-system-variables.html>`__.

For details on how to modify MySQL parameters on the console, see :ref:`Modifying Parameters <rds_configuration>`.

Sensitive Parameters
--------------------

The following parameters can result in system security and stability issues if set improperly:

-  **lower_case_table_names**

   Default value: **1**

   Function: Controls whether database and tables stored on disks are case sensitive. The value **1** indicates that database and table names are case-insensitive and are lowercase by default.

   .. note::

      MySQL 8.0 does not support this parameter.

   Impact: Changing this parameter value may cause primary/standby replication exceptions. Exercise caution when performing this operation.

   -  If you want to change this parameter value from **1** to **0**, change it on read replicas and reboot them first, and then repeat the operations on the primary DB instance.
   -  If you want to change this parameter value from **0** to **1**, change it on the primary DB instance and reboot it first, and then run **SELECT @@GLOBAL.GTID_EXECUTED** on read replicas. Wait until the result set is at least the same as the primary DB instance and then change this parameter value on read replicas and reboot them.

-  **innodb_flush_log_at_trx_commit**

   Default value: **1**

   Function: Controls the balance between strict ACID compliance for commit operations and higher performance. The default setting of **1** is required for full ACID compliance. Logs are written and flushed to disks at each transaction commit. If the value is set to **0**, logs are written and flushed to disks once per second. If the value is set to **2**, logs are written at each transaction commit and flushed to disks every two seconds.

   Impact: If this parameter is not set to **1**, data security is not guaranteed. If the system fails, data may be lost.

-  **sync_binlog**

   Default value: **1**

   Function: Controls how often the MySQL server synchronizes binary logs to the disk. The default setting of **1** requires synchronization of the binary log to the disk at each transaction commit. If the value is set to **0**, synchronization of the binary log to the disk is not controlled by the MySQL server but relies on the OS to flush the binary log to the disk. This setting provides the best performance, but in the event of a power failure or OS crash, all binary log information in **binlog_cache** is lost.

   Impact: If this parameter is not set to **1**, data security is not guaranteed. If the system fails, data may be lost.

-  **innodb_large_prefix**

   Default value: **OFF**

   Function: Specifies the maximum length of a single-column index in an InnoDB table.

   .. note::

      This parameter is available only for MySQL 5.6.

   Impact: Changing this parameter value during DDL execution may cause primary/standby replication exceptions. Exercise caution when performing this operation.

   -  If you want to change this parameter value from **OFF** to **ON**, change it on read replicas first and then on the primary DB instance.
   -  If you want to change this parameter value from **ON** to **OFF**, change it on the primary DB instance first and then on read replicas.

Performance Parameters
----------------------

The following parameters can affect database performance:

-  The values of **innodb_spin_wait_delay** and **query_alloc_block_size** are determined by the DB instance specifications. If you increase their values, database performance may be affected.
-  If **key_buffer_size** is set to a value smaller than **4096**, the parameter modification will fail.
-  If **max_connections** is set to a small value, database access will be affected.
-  The default values of the following parameters are determined by the DB instance specifications: **innodb_buffer_pool_size**, **max_connections**, and **back_log**. These parameter values are **default** before being specified.
-  The values of **innodb_io_capacity_max** and **innodb_io_capacity** are determined by the storage type. These parameter values are **default** before being specified.
