:original_name: rds_migration_mysql.html

.. _rds_migration_mysql:

Migrating Data to RDS for MySQL Using mysqldump
===============================================

Preparing for Data Migration
----------------------------

You can access RDS DB instances through an EIP or through an ECS.

#. Prepare an ECS for accessing DB instances in the same VPC or prepare a device for accessing RDS through an EIP.

   -  To connect to a DB instance through an ECS, you need to create an ECS first.

      For details about how to create and connect to an ECS, see :ref:`How Can I Create and Connect to an ECS? <rds_faq_0057>`

   -  To connect to a DB instance through an EIP, you must:

      a. Bind an EIP to a DB instance. For details, see :ref:`Binding an EIP <rds_public_accessibility__section3199593620428>`.
      b. Ensure that the local device can access the EIP.

#. Install the MySQL client on the prepared ECS or device.

   For details, see :ref:`How Can I Install the MySQL Client? <rds_faq_0027>`

   .. note::

      The MySQL client version must be the same as the version of RDS for MySQL. The MySQL database or client will provide mysqldump and mysql.

      After data is migrated to RDS, you may need to change the IP address. For details, see :ref:`Configuring and Changing a Floating IP Address <rds_05_0024>`.

Exporting Data
--------------

Before migrating data to RDS, you need to export data first.

.. important::

   -  The export tool must match the DB engine version.
   -  Database migration is performed offline. Before the migration, you must stop any applications using the source database.

#. Log in to the ECS or the device that can access RDS.

#. .. _rds_migration_mysql__li16251172911136:

   Use the mysqldump tool to export metadata into an SQL file.

   .. important::

      The MySQL database is required for RDS management. When exporting metadata, do not specify **--all-database**. Otherwise, the MySQL database will be unavailable.

   **mysqldump** **--databases** <*DB_NAME*> **--single-transaction --order-by-primary --hex-blob --no-data --routines --events --set-gtid-purged=OFF** -u <*DB_USER*> **-p -h** <*DB_ADDRESS*> **-P** <*DB_PORT*> **\|sed -e 's/DEFINER[ ]*=[ ]*[^*]*\\*/\\*/' -e 's/DEFINER[ ]*=.*FUNCTION/FUNCTION/' -e 's/DEFINER[ ]*=.*PROCEDURE/PROCEDURE/' -e 's/DEFINER[ ]*=.*TRIGGER/TRIGGER/' -e 's/DEFINER[ ]*=.*EVENT/EVENT/' >** *<BACKUP_FILE>*

   -  *DB_NAME* indicates the name of the database to be migrated.
   -  *DB_USER* indicates the database username.
   -  *DB_ADDRESS* indicates the database address.
   -  *DB_PORT* indicates the database port.
   -  *BACKUP_FILE* indicates the name of the file to which the data will be exported.

   Enter the database password when prompted.

   Example:

   **mysqldump --databases rdsdb --single-transaction --order-by-primary --hex-blob --no-data --routines --events --set-gtid-purged=OFF -u root -p -h 192.168.151.18 -P 3306 \|sed -e 's/DEFINER[ ]*=[ ]*[^*]*\\*/\\*/' -e 's/DEFINER[ ]*=.*FUNCTION/FUNCTION/' -e 's/DEFINER[ ]*=.*PROCEDURE/PROCEDURE/' -e 's/DEFINER[ ]*=.*TRIGGER/TRIGGER/' -e 's/DEFINER[ ]*=.*EVENT/EVENT/' > dump-defs.sql**

   **Enter password:**

   .. note::

      If you use mysqldump with a version earlier than 5.6, remove **--set-gtid-purged=OFF** before running this command.

   After this command is executed, a **dump-defs.sql** file will be generated as follows:

   .. code-block:: console

      [rds@localhost ~]$ ll dump-defs.sql
      -rw-r-----. 1 rds rds 2714 Sep 21 08:23 dump-defs.sql

#. Use the mysqldump tool to export data into an SQL file.

   .. important::

      The MySQL database is required for RDS management. When exporting metadata, do not specify **--all-database**. Otherwise, the MySQL database will be unavailable.

   **mysqldump --databases** <*DB_NAME*> **--single-transaction --hex-blob --set-gtid-purged=OFF --no-create-info --skip-triggers** **-u** <*DB_USER*> **-p** **-h** <*DB_ADDRESS*> **-P** <*DB_PORT*> **-r** <*BACKUP_FILE*>

   For details on the parameters in the preceding command, see :ref:`2 <rds_migration_mysql__li16251172911136>`.

   Enter the database password when prompted.

   Example:

   **mysqldump --databases rdsdb --single-transaction --hex-blob --set-gtid-purged=OFF --no-create-info --skip-triggers -u root -p -h 192.168.151.18 -P 8635 -r dump-data.sql**

   .. note::

      If you use mysqldump with a version earlier than 5.6, remove **--set-gtid-purged=OFF** before running this command.

   After this command is executed, a **dump-data.sql** file will be generated as follows:

   .. code-block:: console

      [rds@localhost ~]$ ll dump-data.sql
      -rw-r-----. 1 rds rds 2714 Sep 21 08:23 dump-data.sql

Importing Data
--------------

You can connect your client to RDS and import exported SQL files into RDS.

.. important::

   If the source database calls triggers, stored procedures, functions, or events, you must set **log_bin_trust_function_creators** to **ON** on the destination database before importing data.

#. Log in to the ECS or the device that can access RDS.

#. Import metadata into RDS.

   # **mysql -f -h** *<RDS_ADDRESS>* **-P** <*DB_PORT*> **-u** root **-p <** *<BACKUP_DIR>*\ **/dump-defs.sql**

   -  *RDS_ADDRESS*: indicates the IP address of the RDS DB instance.
   -  *DB_PORT* indicates the RDS DB instance port.
   -  *BACKUP_DIR* indicates the directory where **dump-defs.sql** is stored.

   Example:

   **# mysql -f -h 172.16.66.198 -P 3306 -u root -p < dump-defs.sql**

   **Enter password:**

   .. note::

      If you intend to import SQL statements of a table to RDS, you are advised to specify a database. Otherwise, the error message "No database selected" may be displayed. For example, if you intend to import SQL statements of a table to database **mydb**, run the following command:

      **# mysql -f -h 172.16.66.198 -P 3306 -u root -p mydb < dump-defs.sql**

      **Enter password:**

#. Import data into RDS.

   # **mysql -f -h** *<RDS_ADDRESS>* **-P** <*DB_PORT*> **-u** root **-p** **<** *<BACKUP_DIR>*\ **/dump-data.sql**

   -  *RDS_ADDRESS*: indicates the IP address of the RDS DB instance.
   -  *DB_PORT* indicates the RDS DB instance port.
   -  *BACKUP_DIR* indicates the directory where **dump-data.sql** is stored.

   Example:

   **# mysql -f -h 172.16.66.198 -P 3306 -u root -p < dump-data.sql**

   **Enter password:**

   .. note::

      If you intend to import SQL statements of a table to RDS, you are advised to specify a database. Otherwise, the error message "No database selected" may be displayed. For example, if you intend to import SQL statements of a table to database **mydb**, run the following command:

      **# mysql -f -h 172.16.66.198 -P 3306 -u root -p mydb < dump-defs.sql**

      **Enter password:**

#. View the import result.

   **mysql> show databases;**

   The following result indicates that database **rdsdb** has been imported.

   .. code-block::

      mysql> show databases;
      +--------------------+
      | Database           |
      +--------------------+
      | information_schema |
      | rdsdb              |
      | mysql              |
      | performance_schema |
      +--------------------+
      4 rows in set (0.00 sec)
