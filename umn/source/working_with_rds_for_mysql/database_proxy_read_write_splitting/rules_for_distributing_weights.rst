:original_name: rds_11_0020.html

.. _rds_11_0020:

Rules for Distributing Weights
==============================

This section describes the rules of distributing read weights to DB instances of different specifications.

Weight Distribution Rules
-------------------------

When the system automatically sets the read weights for DB instances, the weight values are fixed.

.. note::

   The default weight equals to the number of vCPUs multiplied by 50. The weight ranges from 100 to 1000.

Adding a Hint to Specify the Direction that a SQL Statement Will Be Routed
--------------------------------------------------------------------------

Hints supported by read/write splitting are as follows:

-  ``/*FORCE_MASTER*/``: A SQL statement is routed to the primary DB instance.
-  ``/*FORCE_SLAVE*/``: A SQL statement is routed to a read replica.

.. note::

   -  In addition to the weight distribution system of read/write splitting, hints are a useful type of SQL syntax that allows you to specify whether a SQL statement is executed on the primary DB instance or on a read replica.
   -  Hints are only used as routing suggestions. In non-read-only SQL and non-transaction scenarios, SQL statements cannot be routed to read replicas.
