:original_name: rds_09_0043.html

.. _rds_09_0043:

Creating or Deleting a Plugin
=============================

RDS provides the PostgreSQL plugin management solution for user **root**. Except the following plugins, you need to manually create other plugins by referring to this section.

-  auto_explain
-  passwordcheck
-  pg_profile_pro
-  pg_sql_history
-  wal2json
-  test_decoding

.. note::

   The PostgreSQL plugin takes effect at the database level, not globally. You need to manually create it on corresponding databases.

   The latest minor versions of PostgreSQL 11, 12, 13, and 14 allow the **root** user to create plugins (create extension) or delete plugins (drop extension).

Creating a Plugin
-----------------

#. Connect to the database **database1** as user **root** and use **template1** to create a database that can support the plugin.

   **# psql --host=**\ *<RDS_ADDRESS>* **--port=**\ <*DB_PORT*> **--dbname=database1 --username=root -c** "**create database** *<DB_NAME>* **template template1**;"

   -  **RDS_ADDRESS** indicates the IP address of the RDS DB instance.
   -  **DB_PORT** indicates the RDS DB instance port.
   -  **DB_NAME** indicates the name of the database to be created.

   Enter the password of user **root** when prompted.

   Create a database named **my_extension_db** that can support the plugin. Example:

   **# psql --host=192.168.6.141 --port=\ 5432 --dbname=database1 --username=root -c "create database my_extension_db template template1;"**

   .. code-block::

      Password for user root:
      CREATE DATABASE

   Note: If you are creating a database as a common user, log in to the created database as the common user and run the following command to grant all rights to user **root**:

   **GRANT ALL ON DATABASE db1 TO root;**

#. Connect to the created database as user **root** and create a plugin.

   **# psql --host=**\ *<RDS_ADDRESS>* **--port=**\ <*DB_PORT*> **--dbname=**\ *<DB_NAME>* **--username=root -c** "**select control_extension**\ ('**create**','*<EXTENSION_NAME>*');"

   -  **RDS_ADDRESS** indicates the IP address of the RDS DB instance.
   -  **DB_PORT** indicates the RDS DB instance port.
   -  **DB_NAME** indicates the name of the database to be created.
   -  **EXTENSION_NAME** indicates the plugin name. For more information, see :ref:`Supported Plugins <rds_09_0045>`.

   Enter the password of user **root** when prompted.

   Create the postgis plugin in the database **my_extension_db**. Example:

   **# psql --host=192.168.6.141 --port=\ 5432 --dbname=my_extension_db --username=root -c "select control_extension('create','postgis');"**

   .. code-block::

      Password for user root:
            control_extension
      ------------------------------
       create postgis successfully.
      (1 row)

Deleting a Plugin
-----------------

Connect to the database with a plugin created as user **root** and delete the plugin.

**# psql --host=**\ *<RDS_ADDRESS>* **--port=**\ <*DB_PORT*> **--username=root** **--dbname=**\ *<DB_NAME>* **-c** "**select control_extension** ('**drop**','*<EXTENSION_NAME>*');"

-  **RDS_ADDRESS** indicates the IP address of the RDS DB instance.
-  **DB_PORT** indicates the RDS DB instance port.
-  **DB_NAME** indicates the name of the database to be created.
-  **EXTENSION_NAME** indicates the plugin name. For more information, see :ref:`Supported Plugins <rds_09_0045>`.

Enter the password of user **root** when prompted.

Example:

**# psql --host=192.168.6.141 --port=\ 5432 --dbname=my_extension_db --username=root -c "select control_extension('drop','postgis');"**

.. code-block::

   Password for user root:
        control_extension
   ----------------------------
    drop postgis successfully.
   (1 row)
