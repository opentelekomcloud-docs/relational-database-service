:original_name: rds_faq_0025.html

.. _rds_faq_0025:

What Types of DB Engines Does RDS Support for Importing Data?
=============================================================

-  Exporting or importing data between DB engines of the same type is called homogeneous database export or import.

-  Exporting or importing data between DB engines of different types is called heterogeneous database export or import. For example, import data from Oracle to DB engines supported by RDS.

   Generally, data cannot be exported or imported between heterogeneous databases due to the different data formats involved. However, if the data formats are compatible, table data can, in theory, be migrated between them.

   Third-party software is usually required for data replication to export and import between heterogeneous databases. For example, you can use a third-party tool to export table records from Oracle into a .txt file. Then, you can use LOAD statements to import the exported table records to a DB engine supported by RDS.
