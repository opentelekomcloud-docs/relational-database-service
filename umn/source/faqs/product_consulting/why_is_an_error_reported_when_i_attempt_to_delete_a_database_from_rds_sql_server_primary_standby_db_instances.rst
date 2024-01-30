:original_name: rds_faq_0094.html

.. _rds_faq_0094:

Why Is an Error Reported When I Attempt to Delete a Database from RDS SQL Server Primary/Standby DB Instances?
==============================================================================================================

Symptom
-------

An error shown in :ref:`Figure 1 <rds_faq_0094__fig162510431417>` is reported on SQL Server Management Studio when a database is being deleted from RDS SQL Server primary/standby DB instances.

**The database 'xxxx' is enabled for database mirroring. Database mirroring must be removed before you drop the database. Error: 3743**

.. _rds_faq_0094__fig162510431417:

.. figure:: /_static/images/en-us_image_0000001786934021.png
   :alt: **Figure 1** Error information

   **Figure 1** Error information

Possible Causes
---------------

The error details indicate that the SQL Server DB instance type is primary/standby and database mirroring is enabled for the standby DB instance. As a result, the database cannot be deleted.

Solution
--------

Before deleting the database, run the following commands to disable the mirroring:

**Use master**

**go**

**ALTER DATABASE** *[Database_Name]* **SET PARTNER OFF;**

**GO**

Once database mirroring is disabled, the database can be deleted.
