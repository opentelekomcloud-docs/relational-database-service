:original_name: rds_03_0100.html

.. _rds_03_0100:

Downloading a Binlog Backup File
================================

Scenarios
---------

RDS for MySQL allows you to download binlog backup files to your client computer and use them to restore DB instances if necessary. For details, see :ref:`Downloading a Binlog Backup File <rds_03_0100__en-us_topic_0192954021_section61116810348>` or :ref:`Downloading a Merged Binlog <rds_03_0100__section625243344717>`.

.. _rds_03_0100__en-us_topic_0192954021_section61116810348:


Downloading a Binlog Backup File
--------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance. The **Summary** page is displayed.

#. In the navigation pane on the left, choose **Backups & Restorations**. On the **Binlog Backups** page, locate the target backup to be downloaded and click **Download** in the **Operation** column.

   You can also select the binlog backups to be downloaded and click **Download** above the list.

#. After the download is complete, you can view the binlog backups locally.

.. _rds_03_0100__section625243344717:

Downloading a Merged Binlog
---------------------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance. The **Summary** page is displayed.
#. In the navigation pane on the left, choose **Backups & Restorations**. On the **Merged Binlogs** page, select a binlog time range and click **Merge**.

   -  The maximum time range for merging binlogs is 24 hours.
   -  The available time range is consistent with the retention period you have set for the automated backups. For details about how to set the retention period, see :ref:`Configuring an Intra-Region Backup Policy <rds_08_0004>`.

#. During the merging process, the file status is **Merging**. Wait until the status becomes **Merged successfully** and click **Download** in the **Operation** column.
#. In the displayed dialog box, select a download method.

   .. note::

      After the merged file is downloaded, delete it. The system will delete it after 30 days if you do not delete it yourself.

      On the **Merged Binlogs** page, you can locate the target merged binlog to be deleted and click **Delete** in the **Operation** column.

   -  **Use OBS Browser+**

      a. Download OBS Browser+ by following Step 1 provided on the download guide page.

      b. Decompress and install OBS Browser+.

      c. Log in to OBS Browser+ using the username provided in Step 2 on the download guide page.

      d. Add an external bucket using the bucket name provided in Step 2 on the download guide page.

         In the **Add External Bucket** dialog box of OBS Browser+, enter the bucket name provided in step 2 on the download guide page, and click **OK**.

      e. Download a merged binlog.

         On the OBS Browser+ page, click the bucket that you added. In the search box on the right of the object list page, enter the backup file name and start a search. In the search result, locate the target backup and click |image3| in the **Operation** column.

   -  **Use Current Browser**

      Download the merged binlog directly from the current browser.

   -  **Use Download URL**

      Click |image4| to copy the URL within the validity period to download the merged binlog.

      -  You can use other download tools to download the merged binlog.

      -  You can also run the following command to download the merged binlog:

         **wget -O** *FILE_NAME* **--no-check-certificate** **"**\ *DOWNLOAD_URL*\ **"**

         Variables in the commands are as follows:

         *FILE_NAME*: indicates the new name of the merged binlog file. The original backup file name may be too long and exceed the maximum characters allowed by the client file system. You are advised to use the **-O** argument with wget to rename the backup file.

         *DOWNLOAD_URL*: indicates the location of the merged binlog to be downloaded. If the location contains special characters, escape is required.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211679.png
.. |image3| image:: /_static/images/en-us_image_0000002557433943.png
.. |image4| image:: /_static/images/en-us_image_0000002526234126.png
