:original_name: rds_05_0044.html

.. _rds_05_0044:

Restoring from Backup Files to a Self-Built SQL Server Database
===============================================================

You can download backup files by referring to section :ref:`Downloading a Backup File <rds_11_0013>` and restore data from them. You can use SQL Server Management Studio (SSMS) to connect to a self-built ECS database or local database to restore data. The following uses SSMS as an example to show how to restore data from a backup file on a local database.

.. note::

   -  Before restoring data, ensure that the ECS has been installed with the SQL Server database service running a same or later version than the SQL Server databases.

Procedure
---------

#. Download SSMS and upload it to the ECS for installation.

   Download **SSMS 18.0 (GA)** from the `website <https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017>`__ and upload it to the ECS.

#. On the ECS, decompress the RDS full backup file that has been downloaded.

#. Start the SSMS client.

#. Log in to the local database service through the SSMS client.

#. In the SSMS client, right-click **Databases** and choose **Restore Database**.

   |image1|

#. In the displayed **Restore Database** dialog box, select **Device** in the **Source** pane. In the displayed **Select backup devices** dialog box, specify the backup media and its location and click **OK**.

   a. Set **Backup media type** to **File**.

      |image2|

   b. Click **Add** to add the decompressed backup file (in the .bak format) and configure required information on the **Options** page.


      .. figure:: /_static/images/en-us_image_0000001145051704.png
         :alt: **Figure 1** Adding a backup file

         **Figure 1** Adding a backup file


      .. figure:: /_static/images/en-us_image_0000001191131381.png
         :alt: **Figure 2** Configuring required options

         **Figure 2** Configuring required options

   3. Click **OK** to add the backup file to the backup media list and click **OK** again to restore the backup file to a self-built database.

   |image3|

.. |image1| image:: /_static/images/en-us_image_0000001191131383.png
.. |image2| image:: /_static/images/en-us_image_0000001191131379.png
.. |image3| image:: /_static/images/en-us_image_0000001191131385.png
