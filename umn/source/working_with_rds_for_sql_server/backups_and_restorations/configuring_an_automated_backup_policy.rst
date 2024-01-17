:original_name: rds_11_0031.html

.. _rds_11_0031:

Configuring an Automated Backup Policy
======================================

Scenarios
---------

When you create a DB instance, an automated backup policy is enabled by default. For security purposes, the automated backup policy cannot be disabled. After the DB instance is created, you can customize the automated backup policy as required and then RDS backs up data based on the automated backup policy you have set.

RDS automatically backs up data at the DB instance level. If a database is faulty or data is damaged, you can restore it from backups to ensure data reliability. Backups are saved as packages in OBS buckets to ensure data confidentiality and durability. Since backing up data affects the database read and write performance, you are advised to set the automated backup time window to off-peak hours.

The default automated backup policy is as follows:

-  Retention period: 7 days
-  Time window: An hour within 24 hours, such as 01:00-02:00 or 12:00-13:00. The backup time is configured based on UTC time and is adjusted for daylight saving time, which changes at different times depending on the time zone.
-  Backup cycle: Each day of the week

Modifying an Automated Backup Policy
------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. On the **Backups & Restorations** page, click **Modify Backup Policy**.

   -  **Retention Period** refers to the number of days that your automated backups can be retained. Increasing the retention period will improve data reliability.
   -  If you shorten the retention period, the new backup policy takes effect for all backup files. The backup files that have expired will be deleted.
   -  The backup retention period indicates the number of days you want automated full and incremental backups of your DB instance to be retained. It ranges from 1-732 days. The backup time window is one hour. You are advised to select an off-peak time window for automated backups. By default, each day of the week is selected for **Backup Cycle** and you can change it. At least one day must be selected.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
