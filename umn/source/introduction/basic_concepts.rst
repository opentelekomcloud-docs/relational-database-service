:original_name: rds_01_0015.html

.. _rds_01_0015:

Basic Concepts
==============

DB Instances
------------

The smallest management unit of RDS is the DB instance. A DB instance is an isolated database environment on the cloud. Each DB instance runs a DB engine. For details about DB instance types, specifications, engines, versions, and statuses, see :ref:`DB Instance Description <rds_01_0028>`.

DB Engines
----------

RDS supports the following DB engines:

-  MySQL
-  PostgreSQL
-  Microsoft SQL Server

For details about the supported versions, see :ref:`DB Engines and Versions <rds_01_0021>`.

DB Instance Types
-----------------

RDS DB instances are classified into the following types: single and primary/standby.

For details about DB instance types, see :ref:`DB Instance Introduction <rds_01_0010>` and :ref:`Function Comparison <rds_00_0011>`.

DB Instance Classes
-------------------

The DB instance class determines the compute (vCPUs) and memory capacity (memory size) of a DB instance. For details, see :ref:`DB Instance Classes <rds_01_0029>`.

Automated Backups
-----------------

When you create a DB instance, an automated backup policy is enabled by default. After the DB instance is created, you can modify the policy. RDS will automatically create full backups for DB instances based on your settings.

Manual Backups
--------------

Manual backups are user-initiated full backups of DB instances. They are retained until you delete them manually.

Regions and AZs
---------------

A region and availability zone (AZ) identify the location of a data center. You can create resources in a specific region and AZ.

-  Regions are defined in terms of their geographical location and network latency. Each region is completely independent, improving fault tolerance and stability. After a resource is created, its region cannot be changed.
-  An AZ is a physical location using independent power supplies and networks. Faults in an AZ do not affect other AZs. A region can contain multiple AZs, which are physically isolated but interconnected through internal networks. This ensures the independence of AZs and provides low-cost and low-latency network connections.

:ref:`Figure 1 <rds_01_0015__fig2922183194716>` shows the relationship between regions and AZs.

.. _rds_01_0015__fig2922183194716:

.. figure:: /_static/images/en-us_image_0000001145051596.png
   :alt: **Figure 1** Regions and AZs

   **Figure 1** Regions and AZs

Projects
--------

Projects are used to group and isolate OpenStack resources (compute, storage, and network resources). A project can be a department or a project team. Multiple projects can be created for a single account.
