:original_name: rds_09_0062.html

.. _rds_09_0062:

Using pgvector
==============

Introduction
------------

RDS for PostgreSQL supports the **pgvector** plugin, which allows for vector data type and vector similarity search. This plugin supports:

-  Exact and approximate nearest neighbor search
-  L2 distance, inner product, and cosine distance
-  Any language with a PostgreSQL client

For more information, see `official pgvector documentation <https://github.com/pgvector/pgvector>`__.

Supported Versions
------------------

This plugin is available to the latest minor versions of RDS for PostgreSQL 12, 13, and 14. You can run the following SQL statement to check whether your DB instance supports this plugin:

.. code-block:: text

   SELECT * FROM pg_available_extension_versions WHERE name = 'vector';

If this plugin is not supported, :ref:`upgrade the minor version of your DB instance <rds_pg_05_0003>`.

For details about the plugins supported by RDS for PostgreSQL, see :ref:`Supported Plugins <rds_09_0045>`.

Plugin Installation and Uninstallation
--------------------------------------

-  Installing the plugin

   .. code-block:: text

      SELECT control_extension ('create', 'vector');

-  Deleting the plugin

   .. code-block:: text

      SELECT control_extension ('drop', 'vector');

For more information, see :ref:`Installing and Uninstalling a Plugin Using SQL Commands <rds_09_0043>`.

Basic Usage
-----------

-  Creating a vector column with 3 dimensions

   .. code-block:: text

      CREATE TABLE items (id bigserial PRIMARY KEY, embedding vector(3));

-  Inserting vectors

   .. code-block:: text

      INSERT INTO items (embedding) VALUES ('[1,2,3]'), ('[4,5,6]');

-  Getting the nearest neighbors by L2 distance

   .. code-block:: text

      SELECT * FROM items ORDER BY embedding <-> '[3,1,2]';

-  Getting the nearest neighbors by cosine distance

   .. code-block:: text

      SELECT * FROM items ORDER BY embedding <=> '[3,1,2]';

-  Getting the nearest neighbors by inner product

   <#> returns the negative inner product since PostgreSQL only supports ASC order index scans on operators.

   .. code-block:: text

      SELECT * FROM items ORDER BY embedding <#> '[3,1,2]';

Advanced Usage
--------------

-  Getting the distance

   .. code-block:: text

      SELECT embedding <-> '[3,1,2]' AS distance FROM items;
      SELECT (embedding <#> '[3,1,2]') * -1 AS inner_product FROM items;
      SELECT 1 - (embedding <=> '[3,1,2]') AS cosine_similarity FROM items;

-  Averaging vectors

   .. code-block:: text

      SELECT AVG(embedding) FROM items;

-  Exact search providing perfect recall

   You can add an index to use approximate nearest neighbor search, which trades some recall for performance.

   .. code-block:: text

      CREATE INDEX ON items USING ivfflat (embedding vector_l2_ops) WITH (lists = 1);
      INSERT INTO items (embedding) VALUES ('[1,2,4]');
      SELECT * FROM items ORDER BY embedding <-> '[3,3,3]';
