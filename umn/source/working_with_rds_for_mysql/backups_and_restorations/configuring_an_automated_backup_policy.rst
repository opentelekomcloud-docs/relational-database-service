:original_name: rds_08_0004.html

.. _rds_08_0004:

Configuring an Automated Backup Policy
======================================

Scenarios
---------

When you create a DB instance, an automated backup policy is enabled by default. For security purposes, the automated backup policy cannot be disabled. After the DB instance is created, you can customize the automated backup policy as required and then RDS backs up data based on the automated backup policy you configure.

RDS backs up data at the DB instance level, rather than the database level. If a database is faulty or data is damaged, you can restore it from backups. Backups are saved as packages in OBS buckets to ensure data confidentiality and durability. Since backing up data affects database read and write performance, the automated backup time window should be set to off-peak hours.

The automated backup policy is enabled by default as follows:

-  Retention period: 7 days
-  Time window: An hour within 24 hours, such as 01:00-02:00 or 12:00-13:00. The backup time is configured based on UTC time and is adjusted for daylight saving time, which changes at different times depending on the time zone.
-  Backup cycle: Each day of the week by default

Constraints
-----------

-  The number of tables in a DB instance affects the backup speed. The maximum number of tables is 500,000.
-  The system verifies the connection to the DB instance when starting a full backup task. If either of the following conditions is met, the verification fails and a retry is automatically performed. If the retry fails, the backup will fail.

   -  DDL operations are being performed on the DB instance.
   -  The backup lock failed to be obtained from the DB instance.

Modifying an Automated Backup Policy
------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. On the **Backups & Restorations** page, click **Modify Backup Policy**.

   -  **Retention Period** is the number of days that your automated backups are saved for. Increasing the retention period will improve data reliability.
   -  If you shorten the retention period, the new backup policy takes effect for all backup files. Any backup files that have expired, based on a newly configured retention period, will be deleted.
   -  The backup retention period is the number of days you want automated full backups and binlog backups of your DB instance to be saved for. It ranges from 1-732 days. The backup time window is one hour. You are advised to select an off-peak time window for automated backups. By default, each day of the week is selected for **Backup Cycle** and you can change it. At least one day must be selected.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
