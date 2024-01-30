:original_name: rds_09_0009.html

.. _rds_09_0009:

Updating Database Statistics
============================

Scenarios
---------

You can use a stored procedure to update statistics to improve query performance.

Prerequisites
-------------

An RDS Microsoft SQL Server DB instance has been connected. For details about how to connect to a DB instance, see :ref:`Connecting to a DB Instance Through a Public Network <rds_03_0007>`.

Procedure
---------

Run the following command to update statistics on all databases by default:

**EXEC rdsadmin.dbo.rds_updatestats** ;

Run the following command to update statistics on a specified database:

**EXEC rdsadmin.dbo.rds_updatestats** '*@DBname'* ;

The ***@DBname'*** parameter indicates the name of the database whose statistics are to be updated.

Example:

**EXEC rdsadmin.dbo.rds_updatestats** '*MyTestDb'* ;

After the database statistics are updated, the system displays the following information:

|image1|

.. |image1| image:: /_static/images/en-us_image_0000001739814720.png
