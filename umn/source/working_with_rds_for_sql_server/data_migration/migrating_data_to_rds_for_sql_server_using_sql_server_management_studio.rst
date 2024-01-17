:original_name: rds_10_0035.html

.. _rds_10_0035:

Migrating Data to RDS for SQL Server Using SQL Server Management Studio
=======================================================================

Preparing for Data Migration
----------------------------

You can access RDS DB instances through an EIP or ECS.

#. Prepare an ECS for accessing DB instances in the same VPC or prepare a device for accessing RDS through an EIP.

   -  To connect to a DB instance through an ECS, you must first create an ECS.

      For details about how to create and connect to an ECS, see section :ref:`How Can I Create and Connect to an ECS? <rds_faq_0057>`

   -  To connect to a DB instance through an EIP, you must:

      a. Bind the EIP to the DB instance. For details, see :ref:`Binding an EIP <rds_public_accessibility__section3199593620428>`.
      b. Ensure that the local device can access the EIP that has been bound to the DB instance.

#. Install the Microsoft SQL Server client on the ECS or the device.

   For details, see :ref:`How Can I Install SQL Server Management Studio? <rds_faq_0032>`

   .. note::

      The SQL Server Management Studio version must be equal to or later than the Microsoft SQL Server DB engine version.

Exporting Data
--------------

Before migrating an existing Microsoft SQL Server database to RDS, you need to export the Microsoft SQL Server database.

.. important::

   -  The export tool must match the DB engine version.
   -  Database migration is performed offline. Before the migration, you must stop any applications using the source database.

#. Log in to the ECS or device that can access RDS.

#. Use SQL Server Management Studio to generate database object scripts such as tables and views.

   a. Use SQL Server Management Studio to connect to the Microsoft SQL Server database.
   b. On **Object Explorer**, expand **Databases**, right-click the database to be exported, and choose **Tasks** > **Generate Scripts**. The **Generate and Publish Scripts** window is displayed.
   c. Choose **Choose Objects** in the navigation pane on the left, select database objects to be exported, and click **Next**.
   d. Choose **Set Scripting Options** in the navigation pane on the left, click **Save script to a specific location**, and select a path for storing exported files from the **File name** drop-down list, and click **Next**.

      .. note::

         -  If you select **Single file**, all objects will be stored in the same file.
         -  If you select **Single file per object**, each object will be stored in its own file.

   e. Click **Next**.
   f. Click **Finish**.
   g. Use SQL Server Management Studio to open the exported SQL file or SQL files.
   h. Change **USE [DATABASE]** in the first line to **USE [RDS database name]** and save the change.

   .. note::

      For details on generating scripts, see `Generate and Publish Scripts Wizard <https://docs.microsoft.com/en-us/sql/ssms/scripting/generate-and-publish-scripts-wizard?view=sql-server-2017>`__.

#. Use bcp to export data from the source database to a .txt file.

   Download and install the `bcp <https://docs.microsoft.com/en-us/sql/tools/bcp-utility?view=sql-server-2017>`__ first. The command for exporting data is as follows:

   **>bcp** *dbname.schema_name.table_name* **out** *C:\\test\\table_name.txt* **-n** **-S** localhost **-U** *username* **-b** *2000*

   -  **out** indicates the directory from which the data is imported.
   -  **-n** indicates that the native (database) data types are used for performing bulk-copy operations.
   -  **-S** indicates the address to be used by the bcp tool to connect to the Microsoft SQL Server DB instance.
   -  **-U** indicates the database username.
   -  **-b** indicates the lines of data imported in a batch.

   Enter the database password when prompted.

   Example:

   .. code-block::

      C:\test>bcp test.dbo.t1 out c:\test\t1.txt -n -S localhost -U rdsuser -b 2000
      Enter password:

   After this command is executed, a **t1.txt** file will be generated as follows:

   .. code-block::

      C:\test>$ dir t1.txt
      2017/03/27  11:51         22 t1.txt

   Repeat the preceding steps to export data from the other tables in the database.

Importing Data
--------------

This section describes how to use an ECS or a device that can access RDS to connect to a DB instance and import the exported SQL file into RDS.

.. important::

   If the source database contains the full-text index, you need to create one on RDS.

#. Import data through tools.

   Method 1: Use sqlcmd to import database objects.

   The Microsoft SQL Server database or client provides sqlcmd.

   >\ **sqlcmd -S** "*server*" **-d** *database* **-U** *login_id* **-i** *inputfile*

   -  **-S** indicates the IP address and port of the RDS DB instance.
   -  **-d** indicates the name of the database to be imported.
   -  **-U** indicates the username used to log in to the database.
   -  **-i** indicates the SQL file to be executed.

   Enter the database password when prompted.

   Example:

   .. code-block::

      >sqlcmd -S "10.65.60.79,8636" -d test -U rdsuser -i C:\test\objects.sql
      Enter password:

   Method 2: Use bcp to import data.

   >\ **bcp** *dbname.schema_name.table_name* **in** *C:\\test\\table_name.txt* **-n -S** *Server* **-U** *username* **-b** *2000*

   -  **in** indicates the directory which the data is imported to.
   -  **-n** indicates that the native (database) data types are used for performing bulk-copy operations.
   -  **-S** indicates the address to be used by the bcp tool to connect to the Microsoft SQL Server DB instance.
   -  **-U** indicates the database username.
   -  **-b** indicates the lines of data imported in a batch.

   Enter the database password when prompted.

   Example:

   .. code-block::

      C:\test>bcp test.dbo.t1 in c:\test\t1.txt -n -S "10.65.60.79,8636" -U rdsuser -b 2000
      Enter password:

#. Check the data import result.

   .. code-block:: text

      select * from sys.databases;


   .. figure:: /_static/images/en-us_image_0000001145211626.png
      :alt: **Figure 1** Data import result

      **Figure 1** Data import result
