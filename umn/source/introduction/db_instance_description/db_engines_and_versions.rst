:original_name: en-us_topic_0043898356.html

.. _en-us_topic_0043898356:

DB Engines and Versions
=======================

:ref:`Table 1 <en-us_topic_0043898356__table1539112616503>` lists the DB engines and versions supported by RDS.

For new applications, you are advised to use the latest major version of the DB engine, for example, MySQL 8.0. When you create a DB instance, you can select a major DB engine version only (such as MySQL 8.0). The system will automatically select an appropriate minor version (such as 8.0.17) for you. After the DB instance is created, you can view the minor version in the **DB Engine Version** column on the **Instances** page. The DB engine and version vary according to site requirements.

.. _en-us_topic_0043898356__table1539112616503:

.. table:: **Table 1** DB engines and versions

   +----------------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+-----------------+
   | DB Engine            | Single                                                                                                            | Primary/Standby                                                                                                   | Cluster         |
   +======================+===================================================================================================================+===================================================================================================================+=================+
   | MySQL                | -  8.0                                                                                                            | -  8.0                                                                                                            | Not supported   |
   |                      | -  5.7                                                                                                            | -  5.7                                                                                                            |                 |
   |                      | -  5.6                                                                                                            | -  5.6                                                                                                            |                 |
   +----------------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+-----------------+
   | PostgreSQL           | -  Enhanced Edition (PostgreSQL 1.0). For more information, see :ref:`PostgreSQL Enhanced Edition <rds_04_0001>`. | -  Enhanced Edition (PostgreSQL 1.0). For more information, see :ref:`PostgreSQL Enhanced Edition <rds_04_0001>`. | Not supported   |
   |                      | -  13                                                                                                             | -  13                                                                                                             |                 |
   |                      | -  12                                                                                                             | -  12                                                                                                             |                 |
   |                      | -  11                                                                                                             | -  11                                                                                                             |                 |
   |                      | -  10                                                                                                             | -  10                                                                                                             |                 |
   |                      | -  9.6                                                                                                            | -  9.6                                                                                                            |                 |
   |                      | -  9.5                                                                                                            | -  9.5                                                                                                            |                 |
   +----------------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+-----------------+
   | Microsoft SQL Server | -  2017 SE                                                                                                        | -  2017 SE                                                                                                        | -  2017 EE      |
   |                      | -  2016 EE                                                                                                        | -  2016 EE                                                                                                        |                 |
   |                      | -  2016 SE                                                                                                        | -  2016 SE                                                                                                        |                 |
   |                      | -  2014 SE                                                                                                        | -  2014 SE                                                                                                        |                 |
   +----------------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+-----------------+