:original_name: rds_09_0023.html

.. _rds_09_0023:

Migrating Data to RDS for PostgreSQL Using psql
===============================================

Preparing for Data Migration
----------------------------

PostgreSQL supports logical backups. You can use the pg_dump logical backup function to export backup files and then import them to RDS using psql.

You can access RDS DB instances through an EIP or through an ECS.

Preparations
------------

#. Prepare an ECS for accessing DB instances in the same VPC or prepare a device for accessing RDS through an EIP.

   -  To connect to a DB instance through an ECS, you need to create an ECS first.

      For details about how to create and connect to an ECS, see section :ref:`How Can I Create and Connect to an ECS? <rds_faq_0057>`

   -  To connect to a DB instance through an EIP, you must:

      a. Bind an EIP to a DB instance. For details, see :ref:`Binding an EIP <rds_public_accessibility__section3199593620428>`.
      b. Ensure that the local device can access the EIP that has been bound to the DB instance.

#. Install the PostgreSQL client on the prepared ECS or device.

   For details, see :ref:`How Can I Install the PostgreSQL Client? <rds_faq_0029>`

   .. note::

      The PostgreSQL client version must be the same as the version of RDS for PostgreSQL. The PostgreSQL database or client will provide pg_dump and psql.

Exporting Data
--------------

Before migrating an existing PostgreSQL database to RDS, you need to export the PostgreSQL database.

.. important::

   -  The export tool must match the DB engine version.
   -  Database migration is performed offline. Before the migration, you must stop any applications using the source database.

#. Log in to the ECS or the device that can access RDS.

#. Use the pg_dump tool to export the source database into an SQL file.

   **pg_dump** **--username=**\ *<DB_USER>* **--host=**\ *<DB_ADDRESS>* **--port=**\ *<DB_PORT>* **--format=plain --file=**\ *<BACKUP_FILE>* *<DB_NAME>*

   -  **DB_USER** indicates the database username.
   -  **DB_ADDRESS** indicates the database address.
   -  **DB_PORT** indicates the database port.
   -  **BACKUP_FILE** indicates the name of the file to which the data will be exported.
   -  **DB_NAME** indicates the name of the database to be migrated.

   Enter the database password when prompted.

   Example:

   **$ pg_dump --username=root --host=192.168.151.18 --port=\ 5432 --format=plain --file=backup.sql my_db**

   **Password for user root:**

   After this command is executed, a **backup.sql** file will be generated as follows:

   [rds@localhost ~]$ ll backup.sql

   .. code-block::

      -rw-r-----. 1 rds rds 2714 Sep 21 08:23 backup.sql

Importing Data
--------------

#. Log in to the ECS or the device that can access RDS.

#. Ensure that the destination database to which data is to be imported exists.

   If the destination database does not exist, run the following command to create a database:

   **# psql --host=**\ *<RDS_ADDRESS>* **--port=**\ <*DB_PORT*> **--username=**\ *root* **--dbname=postgres** **-c** "**create database** *<DB_NAME>*;"

   -  **RDS_ADDRESS** indicates the IP address of the RDS DB instance.
   -  **DB_PORT** indicates the RDS DB instance port.
   -  **DB_NAME** indicates the name of the database to be imported.

#. Import the exported file to RDS.

   **# psql --host=**\ *<RDS_ADDRESS>* **--port=**\ <*DB_PORT*> **--username=**\ *root* **--dbname=**\ *<DB_NAME>* **--file=**\ *<BACKUP_DIR>*/backup.sql

   -  **RDS_ADDRESS** indicates the IP address of the RDS DB instance.
   -  **DB_PORT** indicates the RDS DB instance port.
   -  **DB_NAME** indicates the name of the database to which data is to be imported. Ensure that the database exists.
   -  **BACKUP_DIR** indicates the directory where the **backup.sql** file is stored.

   Enter the password for the RDS DB instance when prompted.

   Example:

   **# psql --host=172.16.66.198 --port=\ 5432 --username=root --dbname=my_db --file=backup.sql**

   **Password for user root:**

#. View the import result.

   **my_db=> \\l my_db**

   In this example, the database named **my_db** has been imported.

   .. code-block::

      my_db=> \l my_db
      List of databases
      Name  | Owner | Encoding | Collate     | Ctype       | Access privileges
      ------+-------+----------+-------------+-------------+-----------
      my_db | root  | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
      (1 row)
