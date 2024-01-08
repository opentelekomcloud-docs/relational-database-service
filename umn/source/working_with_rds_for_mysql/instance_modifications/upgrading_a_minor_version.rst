:original_name: rds_05_0003.html

.. _rds_05_0003:

Upgrading a Minor Version
=========================

Scenarios
---------

RDS for MySQL supports minor version upgrades to improve performance, add new functions, and fix bugs.

Precautions
-----------

-  The upgrade will cause the DB instance to reboot and interrupt services intermittently. To limit the impact of the upgrade, perform the upgrade during off-peak hours, or ensure that your applications support automatic reconnection.
-  If primary and standby DB instances are deployed in the same AZ, a minor version upgrade will trigger a failover. If primary and standby DB instances are deployed in different AZs, a minor version upgrade will trigger two failovers.
-  When you upgrade a minor version of a primary DB instance, minor versions of read replicas (if any) will also be upgraded automatically (they cannot be upgraded separately). Perform the upgrade during off-peak hours because the DB instance will be rebooted after the upgrade is complete.
-  A minor version upgrade cannot be rolled back after the upgrade is complete. If the upgrade fails, the DB instance will be automatically rolled back to the source version.
-  DDL operations, such as create event, drop event, and alter event, are not allowed during a minor version upgrade.

Constraints
-----------

-  If the replication delay between primary and standby DB instances is longer than 300 seconds, the minor version cannot be upgraded.
-  Minor versions cannot be upgraded for DB instances with abnormal nodes.
-  Currently, RDS for MySQL supports a maximum of 100,000 tables. If there are more than 100,000 tables, the minor version upgrade may fail.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target primary/standby DB instances.
#. In the **DB Information** area on the **Basic Information** page, click **Upgrade** in the **DB Engine Version** field.
#. In the displayed dialog box, select a scheduled time and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001744574182.png
