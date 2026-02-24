:original_name: rds_08_0028.html

.. _rds_08_0028:

Managing Storage Capacity
=========================

Function Description
--------------------

Data and log storage space and its changes significantly impact database performance. RDS for MySQL shows you the distribution and changes of used storage on the **Storage Analysis** page. It also provides storage autoscaling, intelligent tablespace diagnosis, and analysis of top 50 largest databases and tables.

.. table:: **Table 1** Functions

   +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Function                                | Description                                                                                                                                                   | Related Operations                                                                                                      |
   +=========================================+===============================================================================================================================================================+=========================================================================================================================+
   | Overview                                | You can view storage usage, available storage, total storage, daily increase in the last week, and estimated available days of storage.                       | :ref:`Viewing the Storage Overview <rds_08_0028__en-us_topic_0000001372652665_section31122507225>`                      |
   +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Tablespaces                             | It shows you tables with abnormal tablespace growth, tables without primary keys, and tables without indexes.                                                 | :ref:`Tablespaces <rds_08_0028__en-us_topic_0000001372652665_section188641051182316>`                                   |
   +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Used Storage and Used Storage over Time | You can view the distribution of storage space and its changes over time.                                                                                     | :ref:`Disk Space Distribution <rds_08_0028__en-us_topic_0000001372652665_section0680202312019>`                         |
   +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Top Databases and Tables                | You can view the top 50 databases and tables by physical file size and identify the databases and tables with high usage based on storage space distribution. | :ref:`Top Databases and Tables by Physical File Size <rds_08_0028__en-us_topic_0000001372652665_section41131039162912>` |
   +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+

.. _rds_08_0028__en-us_topic_0000001372652665_section31122507225:

Viewing the Storage Overview
----------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance name.

#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.

#. Click the **Storage Analysis** tab to view storage usage. If your storage is insufficient, scale it up. Or you can :ref:`enable storage autoscaling <rds_05_0039>`.

   If the average daily increase in last week is 0 GB, the estimated available days of storage are unlimited and are not displayed.

.. _rds_08_0028__en-us_topic_0000001372652665_section188641051182316:

Tablespaces
-----------

This function counts tables with abnormal tablespace growth, tables without primary keys, and tables without indexes. To use this function, subscribe to Intelligent O&M first.

#. Click the **Storage Analysis** tab to view abnormal tables.

#. Click **Subscribe**. In the displayed dialog box, you can learn about Intelligent O&M functions and pricing.

#. After subscribing to Intelligent O&M, view the table diagnosis results of your instance.

#. Click |image2| next to **Auto Diagnosis**. In the displayed dialog box, configure the daily tablespace increase limit and click **OK**.

   When the size of a single table is greater than the threshold, the system automatically filters the table and collects statistics on the number of such tables on the **Tablespaces** page. The system filters tables once a day.

.. _rds_08_0028__en-us_topic_0000001372652665_section0680202312019:

Disk Space Distribution
-----------------------

You can view storage space distribution of your instance.

.. note::

   If the total number of files in your disk space (including data space, binlog space, slow query log space, relay log space, audit log space, temporary space, and other space) exceeds 10,000, RDS will not collect information about the files or display disk space distribution and usages over time on the console. This prevents performance slowdowns caused by collecting statistics on too many files. If this happens, contact technical support.

-  **Data space**: Disk space occupied by user data (including temporary table files)
-  **Binlog**: Disk space occupied by binlogs
-  **Slow query log**: Disk space occupied by slow logs
-  **Relay log**: Disk space occupied by relay logs
-  **Audit log**: Disk space occupied by audit logs
-  **Temporary space**: Disk space occupied by temporary files
-  **Other**: Disk space occupied by files such as **ib_buffer_pool**, **ib_doublewrite**, and **error.log** generated by the instance.

.. _rds_08_0028__en-us_topic_0000001372652665_section41131039162912:

Top Databases and Tables by Physical File Size
----------------------------------------------

You can view the top 50 databases and tables by physical file size and identify the databases and tables with high usage based on storage space distribution.

.. note::

   -  Physical file sizes are precisely recorded, but other fields' values are estimated. If there is a large gap between a file size and another field, run ANALYZE TABLE on the table.
   -  A database or table whose name contains reserved special characters, including slashes (/) and #p#p, is not counted. #p#p identifies the table as a partitioned table.
   -  Top databases and tables are available only in RDS for MySQL 5.7 and 8.0.
   -  If the instance memory usage is greater than 85% or there are more than 50,000 tables in your instance, to prevent data collection from affecting the instance performance, top databases and tables will not be counted.

Click **View Chart** to view data volume changes in the last 7 days, last 30 days, or a custom time period (spanning no more than 30 days).

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000002390250337.png
