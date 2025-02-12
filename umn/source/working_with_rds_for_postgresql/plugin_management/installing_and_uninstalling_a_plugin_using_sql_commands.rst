:original_name: rds_09_0043.html

.. _rds_09_0043:

Installing and Uninstalling a Plugin Using SQL Commands
=======================================================

RDS provides the PostgreSQL plugin management solution for user **root**. Except the following plugins, you need to manually create other plugins by referring to this section.

-  auto_explain
-  passwordcheck
-  pg_profile_pro
-  pg_sql_history
-  plpgsql
-  wal2json
-  test_decoding

.. note::

   -  RDS for PostgreSQL plugins only take effect on the databases you created the plugins for. To use a plugin on databases, it has to be created separately for each database.
   -  The latest minor versions of RDS for PostgreSQL 12, 13, and 14 allow the **root** user to create plugins (create extension) or delete plugins (drop extension).

Creating a Plugin
-----------------

Connect to the database where a plugin needs to be created as user **root** and run the following SQL statements:

**select control_extension('create','**\ *<EXTENSION_NAME>*\ **', '**\ *<SCHEMA>*\ **');**

-  *EXTENSION_NAME* indicates the plugin name. For more information, see :ref:`Supported Plugins <rds_09_0045>`.
-  *SCHEMA* indicates the name of the schema where the plugin is created. If this parameter is not specified, the **public** schema is used by default.

Example:

Create postgis in the public schema.

.. code-block:: text

   -- Specify the public schema for creating the plugin.
   select control_extension('create','postgis', 'public');
          control_extension
    ------------------------------
     create postgis successfully.
    (1 row)
   -- If the schema parameter is not specified, the default schema is public.
   select control_extension('create', 'postgis');
         control_extension
   ------------------------------
    create postgis successfully.
   (1 row)

Deleting a Plugin
-----------------

Connect to the database where a plugin needs to be created as user **root** and run the following SQL statements:

**select control_extension('drop','**\ *<EXTENSION_NAME>*\ **', '**\ *<SCHEMA>*\ **');**

-  *EXTENSION_NAME* indicates the plugin name. For more information, see :ref:`Supported Plugins <rds_09_0045>`.
-  SCHEMA indicates the schema name. This parameter does not matter much when you delete a plugin, so you do not need to specify this parameter.

Example:

.. code-block:: text

   select control_extension('drop','postgis');
         control_extension
    ----------------------------
     drop postgis successfully.
    (1 row)

Common Errors
-------------

-  Error 1

   .. code-block::

      ERROR:  permission denied for function control_extension

   Solution: Use **root** to run the **control_extension** function.

-  Error 2

   .. code-block::

      ERROR:  function control_extension(unknown, unknown) is not unique

   Solution: Add the schema parameter in the function. If the schema is not specified, there may be functions with the same name, causing execution failures.

-  Error 3

   .. code-block::

      ERROR:  function control_extension(unknown, unknown) does not exist

   Solution: Do not create plugins in the **postgres** database. The **control_extension** function does not exist in the **postgres** database because this database is used as an O&M database.
