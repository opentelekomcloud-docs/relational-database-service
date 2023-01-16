:original_name: rds_08_0006.html

.. _rds_08_0006:

Downloading a Backup File
=========================

Scenarios
---------

This section describes how to download a manual or an automated backup file to a local device and restore data from the backup file.

RDS for MySQL enables you to download full backup files.

Constraints
-----------

-  If the size of the backup data is greater than 400 MB, you are advised to use OBS Browser+ to download the backup data.

Method 1: Using OBS Browser+
----------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Backup Management** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

   Alternatively, click the target DB instance. In the navigation pane on the left, choose **Backups & Restorations**. On the **Full Backups** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

#. In the displayed dialog box, select **Use OBS Browser+** for **Download Method** and click **OK**.

   a. Download OBS Browser+

   b. Decompress and install OBS Browser+.

   c. Log in to OBS Browser+.

      For details about how to log in to OBS Browser+, see `Logging In to OBS Browser+ <https://docs.otc.t-systems.com/en-us/usermanual/obs/en-us_topic_0045853477.html>`__ in the *OBS Browser+ Operation Guide*.

   d. Disable certificate verification on OBS Browser+.

      For details on how to configure OBS Browser+, see `Configuring the System <https://docs.otc.t-systems.com/en-us/usermanual/obs/en-us_topic_0045853630.html>`__ in the *OBS Browser+ Operation Guide*.

      .. note::

         The OBS bucket name displayed in the **Download Backup File** pane on the RDS console does not support certificate verification. OBS Browser+ certificate verification needs to be disabled before the external bucket can be added, and then it must be enabled again after the backup is downloaded.

   e. Add an external bucket.

      In the **Add Bucket** dialog box of OBS Browser+, select **Add external bucket** and enter the bucket name provided in step 2 "Add an External Bucket" on the RDS console.

      For details about how to add external buckets, see `Adding External Buckets <https://docs.otc.t-systems.com/en-us/usermanual/obs/en-us_topic_0045853737.html>`__ in the *OBS Browser+ Operation Guide*.

   f. Download the backup file.

      On the OBS Browser+ page, click the bucket that you added. In the search box on the right of OBS Browser+, enter the backup file name provided in step 3 "Download the Backup File" on the RDS console. In the search result, locate the target backup and download it.

   g. After the backup is downloaded, enable OBS Browser+ certificate verification.

#. Follow the instructions provided in :ref:`Restoring from Backup Files to a Self-Built MySQL Database <rds_08_0044>` to restore data locally as required.

Method 2: Using Current Browser
-------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Backup Management** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

   Alternatively, click the target DB instance. In the navigation pane on the left, choose **Backups & Restorations**. On the **Full Backups** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

#. In the displayed dialog box, select **Use Current Browser** for **Download Method** and click **OK**.

#. Follow the instructions provided in :ref:`Restoring from Backup Files to a Self-Built MySQL Database <rds_08_0044>` to restore data locally as required.

Method 3: Using Download URL
----------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Backup Management** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

   Alternatively, click the target DB instance. In the navigation pane on the left, choose **Backups & Restorations**. On the **Full Backups** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

#. In the displayed dialog box, select **Use Download URL** for **Download Method**, click |image4| to copy the URL, and click **OK**.

   A valid URL for downloading the backup data is displayed.

   -  You can use various download tools to download backup files.

   -  You can also run the following command to download backup files:

      **wget -O** *FILE_NAME* **--no-check-certificate** **"**\ *DOWNLOAD_URL*\ **"**

      The parameters in the command are as follows:

      *FILE_NAME*: indicates the new backup file name after the download is successful. The original backup file name may be too long and exceed the maximum characters allowed by the client file system. You are advised to use the **-O** argument with wget to rename the backup file.

      *DOWNLOAD_URL*: indicates the location of the backup file to be downloaded. If the location contains special characters, escape is required.

#. Follow the instructions provided in :ref:`Restoring from Backup Files to a Self-Built MySQL Database <rds_08_0044>` to restore data locally as required.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001470260233.png
.. |image3| image:: /_static/images/en-us_image_0000001470260233.png
.. |image4| image:: /_static/images/en-us_image_0000001470140453.png
