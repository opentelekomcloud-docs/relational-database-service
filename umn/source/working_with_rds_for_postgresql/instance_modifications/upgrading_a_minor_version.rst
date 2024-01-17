:original_name: rds_pg_05_0003.html

.. _rds_pg_05_0003:

Upgrading a Minor Version
=========================

Scenarios
---------

RDS for PostgreSQL supports minor version upgrades to improve performance, add new functions, and fix bugs.

Precautions
-----------

-  When any new minor version is released to address vulnerabilities and other issues from the open source community, :ref:`perform a minor version upgrade <rds_pg_05_0003__section14931659203611>` for your instance.
-  The upgrade will cause the instance to reboot and interrupt services for a period of time. The length of the interruption depends on service volume. To minimize the impact of the upgrade, perform the upgrade during off-peak hours, or ensure that your applications support automatic reconnection.
-  When you upgrade the minor version of a primary instance, the minor versions of read replicas (if any) will also be upgraded automatically. Read replicas cannot be upgraded separately.
-  A minor version upgrade cannot be rolled back after the upgrade is complete. If the upgrade fails, the DB instance will be automatically rolled back to the source version.
-  You are advised to perform a full backup before upgrading a minor version.
-  You need to re-establish a DR relationship after upgrading the minor version of a DR instance.
-  Before upgrading minor versions earlier than RDS for PostgreSQL 12.6, you need to stop all logical replications and delete all logical replication slots. Otherwise, the upgrade will fail.

   -  Querying a replication slot: **select \* from pg_replication_slots;**
   -  Deleting a replication slot: **select pg_drop_replication_slot('SLOT_NAME');**

Constraints
-----------

-  The minor version cannot be upgraded for instances with abnormal nodes.
-  The following minor versions cannot be upgraded:

   -  Versions earlier than 11.2 for RDS for PostgreSQL 11

-  The upgrade will be performed immediately upon the submission of your request. Delayed upgrade of minor versions is not supported.

.. _rds_pg_05_0003__section14931659203611:

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the primary instance name.

#. In the **DB Information** area on the **Basic Information** page, click **Upgrade Minor Version** next to the **DB Engine Version** field.

#. In the displayed dialog box, click **OK**.

   RDS upgrades the minor version to the latest version immediately.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
