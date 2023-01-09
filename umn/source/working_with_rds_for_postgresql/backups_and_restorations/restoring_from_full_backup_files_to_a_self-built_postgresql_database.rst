:original_name: rds_pg_08_0044.html

.. _rds_pg_08_0044:

Restoring from Full Backup Files to a Self-Built PostgreSQL Database
====================================================================

You can download backup files by referring to :ref:`Downloading a Full Backup File <rds_09_0031>` and restore data from them.

Prerequisites
-------------

#. A tool for decompressing TAR files must be installed in a Unix-like system.
#. Either python2.7 or python3 can be used.
#. The following third-party packages need to be installed: lz4, gzip, and shutil.
#. The version of the local database must be the same as that of the cloud database.
#. Plugins of the same version as the cloud database are installed in the local database.

Procedure
---------

#. .. _rds_pg_08_0044__li81101921125518:

   Prepare a local directory for storing tablespaces.

#. Stop the local database server.

#. .. _rds_pg_08_0044__li111172120554:

   Store the following configuration files in the **data** directory of the local database to another directory: **postgresql.conf**, **pg_hba.conf**, and **recovery.done**.

#. Clear the **data** directory of the local database.

#. Download the `decompression tool <https://dbs-download.obs.otc.t-systems.com/rds/pg_restore_file.zip>`__.

#. .. _rds_pg_08_0044__li1450424242419:

   Run the following command to decompress backup files to the directory prepared in Step 1:

   **python restore_obs_file.py** *src_file* *target_dir*

   Variables in the command are described as follows:

   *src_file*: indicates the directory where PostgreSQL full backup files are stored.

   *target_dir*: indicates the directory to which data is restored. The directory has been prepared in :ref:`1 <rds_pg_08_0044__li81101921125518>`. The directory must be empty. If the directory does not exist, the system automatically creates it.

   The following directories are generated after the decompression:

   -  **data**: stores full backup data. The **recovery.done** file has been deleted.
   -  **xlog**: stores incremental backup data.
   -  **tblspc**: stores tablespace directory files (if the original backup contains tablespace files).

#. Copy the files in :ref:`6 <rds_pg_08_0044__li1450424242419>` to the specified directory of the local database.

   a. Copy all the decompressed files in the **data** directory to the **data** directory of the local database, and then replace the three files in the **data** directory of the local database with the configuration files saved in step :ref:`3 <rds_pg_08_0044__li111172120554>`.

   b. Copy the decompressed files in the **xlog** directory to the **pg_xlog** or **pg_wal** folder in the **data** directory of the local database. (The folder names vary according to database versions.)

   c. Move the decompressed tablespace folder (if any) in the **tblspc** directory to the tablespace directory created in step :ref:`1 <rds_pg_08_0044__li81101921125518>` and modify the soft link of the corresponding tablespace in **data\\tablespace_map**.

      |image1|

#. Reboot the database and wait until the database restoration is complete.

.. |image1| image:: /_static/images/en-us_image_0000001470340229.png
