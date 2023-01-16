:original_name: rds_11_0004.html

.. _rds_11_0004:

Configuring the TDE Function
============================

Transparent Data Encryption (TDE) encrypts data files and backup files using certificates to implement real-time I/O encryption and decryption. This function effectively protects the security of databases and data files.

Currently, the TDE function supports single and primary/standby DB instances of the Microsoft SQL Server editions listed in :ref:`Table 1 <rds_11_0004__table118553718299>`.

.. _rds_11_0004__table118553718299:

.. table:: **Table 1** SQL Server editions that support the TDE function

   +-----------------------------------+-----------------------------------+
   | DB Instance Type                  | Editions Support for TDE          |
   +===================================+===================================+
   | Primary/Standby (1/1)             | -  2016 EE                        |
   |                                   | -  2017 SE                        |
   +-----------------------------------+-----------------------------------+
   | Single DB instances               | -  2016 EE                        |
   |                                   | -  2017 SE                        |
   +-----------------------------------+-----------------------------------+
   | Cluster                           | -  2017 EE                        |
   +-----------------------------------+-----------------------------------+

Constraints
-----------

#. If TDE has been enabled for a single DB instance, the instance cannot be changed to primary/standby DB instances.
#. RDS for SQL Server currently does not support TDE certificate download. To restore data offline using the encrypted .bak file, perform the following operations:

   a. Disable TDE for the database. For details, see :ref:`Configuring Database-Level TDE <rds_11_0004__section17914116134615>`.
   b. Create a manual backup for the database.
   c. Restore data from the manual backup.
   d. Enable TDE for the database as required.

#. Enabling TDE improves data security but affects read and write performance of encrypted databases. Exercise caution when enabling TDE.
#. To migrate on-premises encrypted databases to RDS SQL Server DB instances, you need to disable database-level TDE first.
#. DB instances with the instance-level TDE function enabled cannot be restored from backups to existing DB instances.
#. When enabling the instance-level TDE function or using the stored procedure rds_tde to enable or disable database-level TDE, you are advised not to perform the following operations:

   -  Delete files from file groups in databases.
   -  Delete databases.
   -  Take databases offline
   -  Split databases.
   -  Convert databases or file groups to the READ ONLY state.
   -  Run the ALTER DATABASE command.
   -  Create backups.
   -  Start backup for databases or database files.
   -  Start restoration for databases or database files.

Enabling Instance-Level TDE
---------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the **DB Information** area, click |image2| in the **TDE** field to enable TDE.

.. _rds_11_0004__section17914116134615:

Configuring Database-Level TDE
------------------------------

.. note::

   Before enabling the database-level TDE function, ensure that the instance-level TDE function has been enabled.

#. Connect to the target DB instance.

#. Use the stored procedure rds_tde to enable, disable, or query the database-level TDE status.

   **exec master.dbo.rds_tde** *DatabaseName*,\ *TDE_Action*

   -  **DatabaseName**: indicates the target database name, which can be **null**.
   -  *TDE_Action*:

      -  The value **-1** indicates that the database encryption status is queried.

         If **DatabaseName** is **null**, the encryption status of all databases is returned.

      -  The value **0** indicates that the TDE function is disabled.

      -  The value **1** indicates that the TDE function is enabled.

   a. Enable TDE for database db1.

      **exec master.dbo.rds_tde db1, 1**


      .. figure:: /_static/images/en-us_image_0000001420023654.png
         :alt: **Figure 1** Enabling TDE

         **Figure 1** Enabling TDE

   b. Disable TDE for database db1.

      **exec master.dbo.rds_tde db1, 0**


      .. figure:: /_static/images/en-us_image_0000001470140357.png
         :alt: **Figure 2** Disabling TDE

         **Figure 2** Disabling TDE

   c. Query the TDE status of database db1.

      **exec master.dbo.rds_tde db1, -1**


      .. figure:: /_static/images/en-us_image_0000001469940665.png
         :alt: **Figure 3** Querying the TDE status (Enabled)

         **Figure 3** Querying the TDE status (Enabled)


      .. figure:: /_static/images/en-us_image_0000001419863698.png
         :alt: **Figure 4** Querying the TDE status (Disabled)

         **Figure 4** Querying the TDE status (Disabled)

   d. Query the TDE status of all databases.

      **exec master.dbo.rds_tde null, -1**


      .. figure:: /_static/images/en-us_image_0000001470140361.png
         :alt: **Figure 5** Querying the TDE status of all databases

         **Figure 5** Querying the TDE status of all databases

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001470340125.png
