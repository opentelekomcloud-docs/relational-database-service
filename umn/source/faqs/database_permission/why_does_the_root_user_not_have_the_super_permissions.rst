:original_name: rds_faq_0075.html

.. _rds_faq_0075:

Why Does the Root User Not Have the Super Permissions?
======================================================

Most relational database cloud service platforms do not provide super permissions for the **root** user. The super permissions allow users to execute many management commands, such as reset master, set global, kill, and reset slave. These operations may cause primary/standby replication errors. This is a major difference between public cloud databases and on-premises MySQL databases. To ensure stable running of DB instances, RDS does not provide the super permission for the **root** user.

If you need to perform actions that normally require super permissions, RDS provides alternative methods.

For example:

#. You can modify parameter values only on the RDS console. You cannot run the following command on an RDS DB database to modify parameter values.

   **set global parameter name=\ Parameter value;**

   If the script contains the **set global** command, delete the **set global** command and modify parameter values through the RDS console.

#. An error is reported after you run the following command because the **root** user does not have super permissions. You can delete **definer='root'** from the command to solve the problem.

   **create definer='root'@'%' trigger(procedure)...**

   You can import data using mysqldump. For operation details, see :ref:`Migrating Data to RDS for MySQL Using mysqldump <rds_migration_mysql>`.

#. You can create PostgreSQL plugins by referring to :ref:`Creating or Deleting a Plugin <rds_09_0043>`.
