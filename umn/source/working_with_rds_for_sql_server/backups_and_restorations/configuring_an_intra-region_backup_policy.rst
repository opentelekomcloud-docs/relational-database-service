:original_name: rds_11_0031.html

.. _rds_11_0031:

Configuring an Intra-Region Backup Policy
=========================================

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
#. On the **Backups & Restorations** page, in the upper right corner of the page, choose **Modify Backup Policy** > **Configure Same-Region Backup Policy**. On the displayed page, you can view the existing backup policy. If you want to modify the policy, adjust the values of the following parameters:

   -  **Retention Period**: How many days your automated full backups and incremental backups can be retained. The retention period is from 1 to 732 days and the default value is **7**.

      -  Extending the retention period improves data reliability.
      -  Reducing the retention period takes effect for existing backups. Any backups (except manual backups) that have expired will be automatically deleted. Exercise caution when performing this operation.

   -  **Time Window**: A one-hour period the backup will be scheduled for each day, such as 01:00-02:00 or 12:00-13:00. The backup time window indicates when the backup starts. The backup duration depends on the data volume of your instance.

      .. note::

         To minimize the potential impact on services, set the time window to off-peak hours. The backup time is in UTC format. The backup time segment changes with the time zone during the switch between the DST and standard time.

   -  **Backup Cycle**: Daily backups are selected by default, but you can change it. At least one day must be selected.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
