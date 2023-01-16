:original_name: rds_faq_0031.html

.. _rds_faq_0031:

What Inappropriate Parameter Settings Cause Unavailability of the PostgreSQL Database?
======================================================================================

In the following cases, inappropriate parameter settings cause the database to be unavailable:

-  Parameter value ranges are related to DB instance specifications.

   The maximum values of **shared_buffers** and **max_connections** are related to the DB instance physical memory. If you set these parameters inappropriately, the database will be unavailable.

-  Parameter association is incorrect.

   -  If **log_parser_stats**, **log_planner_stats**, or **log_executor_stats** is enabled, you must disable **log_statement_stats**. Otherwise, the database is unavailable.

   -  **max_connections**, **autovacuum_max_workers**, and **max_worker_processes** must meet the following requirements. Otherwise, the database is unavailable.

      **max_connections** value + **autovacuum_max_workers** value + **max_worker_processes** value + 1 < 8388607

.. note::

   For additional details, visit the `PostgreSQL official website <https://www.postgresql.org/docs/current/static/runtime-config.html>`__.

Solution:

#. Log in to the RDS console and query the logs to locate the incorrectly configured parameters.
#. On the **Configuration** page, change parameters to default values and reboot the database.
#. Configure the incorrect parameter values and restore other parameters to their original default values.
