:original_name: rds_09_0064.html

.. _rds_09_0064:

pg_stat_statements
==================

Introduction
------------

The pg_stat_statements extension provides a means for tracking planning and execution statistics of all SQL statements executed by a server.

For more information, see `pg_stat_statements <https://www.postgresql.org/docs/current/pgstatstatements.html>`__ in the PostgreSQL documentation.

Supported Versions
------------------

This extension is available to the latest minor versions of RDS for PostgreSQL 10 and later versions.

You can run the following SQL statement to check whether your DB instance supports this extension:

.. code-block:: text

   SELECT * FROM pg_available_extension_versions WHERE name  = 'pg_stat_statements';

If this extension is not supported, :ref:`upgrade the minor version of your DB instance <rds_pg_05_0003>`.

To see more extensions supported by RDS for PostgreSQL, go to :ref:`Supported Plugins <rds_09_0045>`.

Extension Installation and Uninstallation
-----------------------------------------

To check whether pg_stat_statements is installed in a database, run the following SQL statement:

.. code-block:: text

   select * from pg_extension  where extname = 'pg_stat_statements';

If the command output is empty, the extension is not installed. If the extension information is displayed, the extension is installed.

By default, pg_stat_statements is preloaded in the **shared_preload_libraries** parameter. Perform the following steps to install or delete the extension:

-  Installing the extension

   .. code-block:: text

      SELECT control_extension('create', 'pg_stat_statements');

-  Deleting the extension

   .. code-block:: text

      SELECT control_extension('drop', 'pg_stat_statements');

For more information, see :ref:`Installing and Uninstalling a Plugin on the RDS Console <rds_09_0070>` and :ref:`Installing and Uninstalling a Plugin Using SQL Commands <rds_09_0043>`.

Basic Functions
---------------

#. After the pg_stat_statements extension is installed, configure the parameters below. You can adjust the values based on your workload requirements.

   .. table:: **Table 1** Parameter description

      +-----------------------------------+-----------------+---------------+----------------+---------------------------------------------------------------------------+
      | Parameter                         | Reboot Required | Default Value | Allowed Values | Description                                                               |
      +===================================+=================+===============+================+===========================================================================+
      | pg_stat_statements.max            | Yes             | 5000          | 100-5,000,000  | Specifies the maximum number of statements tracked by pg_stat_statements. |
      +-----------------------------------+-----------------+---------------+----------------+---------------------------------------------------------------------------+
      | pg_stat_statements.save           | No              | on            | on, off        | Specifies whether to save statement statistics across server shutdowns.   |
      +-----------------------------------+-----------------+---------------+----------------+---------------------------------------------------------------------------+
      | pg_stat_statements.track          | No              | top           | top, all, none | Controls which statements are counted by pg_stat_statements.              |
      +-----------------------------------+-----------------+---------------+----------------+---------------------------------------------------------------------------+
      | pg_stat_statements.track_planning | No              | off           | on, off        | Controls whether planning duration is tracked by pg_stat_statements.      |
      +-----------------------------------+-----------------+---------------+----------------+---------------------------------------------------------------------------+
      | pg_stat_statements.track_utility  | No              | on            | on, off        | Controls whether utility commands are tracked by pg_stat_statements.      |
      +-----------------------------------+-----------------+---------------+----------------+---------------------------------------------------------------------------+

#. Query the pg_stat_statements view to obtain statistics.

   .. code-block:: text

      select * from pg_stat_statements;

#. Query the SQL statements with high I/O consumption.

   .. code-block:: text

      -- Top 5 SQL statements
      select userid::regrole, dbid, query
      from pg_stat_statements
      order by (blk_read_time+blk_write_time) desc limit 5;

#. Query the SQL statements with high consumption of shared memory.

   .. code-block:: text

      select userid::regrole, dbid, query
      from pg_stat_statements
      order by (shared_blks_hit+shared_blks_dirtied) desc limit 5;

#. Reset the statistics.

   .. code-block:: text

      select pg_stat_statements_reset();

Advanced Functions
------------------

You can use pg_stat_statements to troubleshoot high CPU usage. The process is as follows:

#. Reset the pg_stat_statements counter.

   .. code-block:: text

      select pg_stat_statements_reset();

   Leave enough time for pg_stat_statements to collect information.

#. Obtain the most time-consuming SQL statements.

   .. code-block:: text

      select * from pg_stat_statements order by total_exec_time desc limit 10;

   The obtained SQL statements have been occupying the user-mode CPU for a long time. Analyze these SQL statements.

#. Obtain the SQL statements that read the buffer for the most times.

   .. code-block:: text

      select * from pg_stat_statements order by shared_blks_hit + shared_blks_read desc limit 10;

   The obtained SQL statements may cause too many buffer reads due to a lack of indexes, consuming a large number of CPU resources.

#. Obtain the SQL statements that have been executed for the most times.

   .. code-block:: text

      select * from pg_stat_statements order by calls desc limit 10;

   It takes a short time to execute some simple SQL statements separately. However, in some cases (for example, cyclic executions in a transaction or concurrent executions), the CPU usage increases.
