:original_name: rds_08_0004.html

.. _rds_08_0004:

Configuring an Intra-Region Backup Policy
=========================================

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
#. On the **Backups & Restorations** page, in the upper right corner of the page, choose **Modify Backup Policy** > **Configure Same-Region Backup Policy**. On the displayed page, you can view the existing backup policy. If you want to modify the policy, adjust the values of the following parameters:

   -  **Retention Period**: It indicates how many days your automated full backups and binlog backups can be retained. The retention period is from 1 to 732 days and the default value is 7.

      -  Extending the retention period enhances data availability.
      -  Reducing the retention period takes effect for existing backups. Any backups (except manual backups) that have expired will be automatically deleted. Exercise caution when performing this operation.

      **Automatic deletion policy for full backups:**

      To ensure data integrity, the system keeps the most recent backup that has exceeded the retention period during automatic deletions. This ensures that data within the retention period can still be restored.

      For example, if **Backup Cycle** was set to **Monday** and **Tuesday** and **Retention Period** was set to **2**, the deletion behavior is as follows:

      -  The full backup created on Monday is automatically deleted on Thursday.

         The full backup created on Monday expires on Wednesday, but according to the deletion policy, the system retains the most recent full backup that has exceeded the retention period. So it is retained until a new backup expires. The next full backup is created on Tuesday and expires on Thursday. Therefore, on Thursday, the Monday backup is deleted and the Tuesday backup is retained.

      -  The full backup created on Tuesday is automatically deleted on Wednesday of the following week.

         The backup generated on Tuesday will expire on Thursday, but as it is the last backup, so it will be retained until a new backup expires. The next backup will be generated on the next Monday and will expire on the next Wednesday. So the full backup generated on Tuesday will not be automatically deleted until the next Wednesday.

   -  **Automatic deletion policy for binlog backups:**

      To ensure data integrity, the system keeps the binlog backup of the previous day when the full backup is deleted. This ensures that data within the retention period can still be restored.

   -  **Time Window**: Set it to a one-hour period the backup will be scheduled, such as 01:00-02:00 or 12:00-13:00. It indicates when the backup starts, not the duration of the entire backup task. The backup duration depends on the data volume of your instance.

      .. note::

         To minimize potential impact on workloads, set the time window to off-peak hours. The backup time window is saved using the UTC time zone of your local browser. It changes with the time zone if the DST or standard time is switched.

   -  **Backup Cycle**: All options are selected by default, but you can change it. Select at least one day of the week.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
