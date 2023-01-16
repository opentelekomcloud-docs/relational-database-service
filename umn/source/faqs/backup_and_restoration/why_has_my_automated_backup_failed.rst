:original_name: rds_faq_0053.html

.. _rds_faq_0053:

Why Has My Automated Backup Failed?
===================================

Automated backups may fail for the following reasons:

#. The network environment is unstable due to issues such as network delay or interruption. RDS will detect these problems and trigger another automated backup half an hour later. You can also perform a manual backup before then.

#. Multi-task executions are complicated, resulting in problems such as task waiting or interruptions. RDS will detect these problems and trigger another automated backup half an hour later. You can also perform a manual backup.

#. A DB instance status is unavailable, possibly because the DB instance is faulty or being modified. RDS will trigger an automated backup when the DB instance status becomes available. You can also perform a manual backup before then.

#. The backup speed depends on how many tables there are in the databases. If the number of tables exceeds 500,000, the backup will fail.

#. A parameter change was incorrect. For example, a DB instance may become faulty after a parameter template containing incorrect parameters was applied to it. You can check whether original and current values are correct, check whether any related parameters also need to be changed, reset the parameter template, or reboot the DB instance.

#. An error occurred during data import.

   For example, system table records get lost due to inappropriate data import.

   For MySQL, you can import data again by referring to section :ref:`Migrating Data to RDS for MySQL Using mysqldump <rds_migration_mysql>`.

   For PostgreSQL, you can import data again by referring to section :ref:`Migrating Data to RDS for PostgreSQL Using psql <rds_09_0023>`.

   For Microsoft SQL Server, you can import data again by referring to section :ref:`Migrating Data to RDS for SQL Server Using SQL Server Management Studio <rds_10_0035>`.

#. If the problem persists, contact technical support.
