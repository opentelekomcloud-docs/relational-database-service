:original_name: rds_09_0044.html

.. _rds_09_0044:

Tablespace Management
=====================

**Scenarios**
-------------

RDS provides the PostgreSQL tablespace management solution based on user **root**.

Creating a Tablespace
---------------------

#. Connect to the database as user **root** and create a tablespace.

   **# psql --host=**\ *<RDS_ADDRESS>* **--port=**\ <*DB_PORT*> **--dbname=**\ *<DB_NAME>* **--username=root -c** "**select control_tablespace** (**'create'**, '*<TABLESPACE_NAME>*');"

   .. table:: **Table 1** Parameter description

      ================= ================================================
      Parameter         Description
      ================= ================================================
      *RDS_ADDRESS*     Indicates the IP address of the RDS DB instance.
      *DB_PORT*         Indicates the port of the RDS DB instance.
      *DB_NAME*         Indicates the database name.
      *TABLESPACE_NAME* Indicates the tablespace name.
      ================= ================================================

#. Enter the password of user **root** when prompted.

   Log in to the **my_db** database and create the **tbspc1** tablespace. Example:

   **# psql --host=192.168.6.141 --port=\ 5432 --dbname=my_db --username=root -c "select control_tablespace('create', 'tbspc1');"**

   .. code-block::

      Password for user root:
                control_tablespace
      ------------------------------
      create tablespace tbspc1 successfully.
      (1 row)

   If the creation fails, view error logs of the DB instance.

   .. note::

      To ensure performance, a maximum of 20 tablespaces can be created.

Deleting a Tablespace
---------------------

#. Connect to a database as user **root** and delete a tablespace.

   **# psql --host=**\ *<RDS_ADDRESS>* **--port=**\ <*DB_PORT*> **--username=root** **--dbname=**\ *<DB_NAME>* **-c** "**select control_tablespace**\ (**'drop',** '*<TABLESPACE \_NAME>*');"

   .. table:: **Table 2** Parameter description

      ================= ================================================
      Parameter         Description
      ================= ================================================
      *RDS_ADDRESS*     Indicates the IP address of the RDS DB instance.
      *DB_PORT*         Indicates the port of the RDS DB instance.
      *DB_NAME*         Indicates the database name.
      *TABLESPACE_NAME* Indicates the tablespace name.
      ================= ================================================

#. Enter the password of user **root** when prompted.

   Example:

   **# psql --host=192.168.6.141 --port=8635 --dbname=my_db --username=root -c "select control_tablespace('drop', 'tbspc1');"**

   .. code-block::

      Password for user root:
               control_tablespace
      ----------------------------
      drop tablespace tbspc1 successfully.
      (1 row)

   Before deleting the tablespace, ensure that it is empty. If the deletion fails, view error logs of the DB instance.
