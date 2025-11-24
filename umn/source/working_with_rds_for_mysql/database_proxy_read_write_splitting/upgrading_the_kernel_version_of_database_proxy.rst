:original_name: rds_11_0024.html

.. _rds_11_0024:

Upgrading the Kernel Version of Database Proxy
==============================================

Scenarios
---------

You can manually upgrade the RDS for MySQL database proxy to the latest kernel version to improve performance, add new functions, and fix problems.

For details about kernel versions, see :ref:`Kernel Versions <rds_11_0027>`.

Upgrade Methods
---------------

A kernel version can be upgraded in either of the following ways:

-  Upon submission: The system :ref:`upgrades the proxy instance version <rds_11_0024__section9833938144>` immediately after you submit the upgrade request.
-  In maintenance window: When you submit an upgrade request, the system waits for a maintenance window to perform the upgrade. For details on how to change the maintenance window, see :ref:`Changing the Maintenance Window <rds_05_0038>`.

If the kernel version of your instance has potential risks or major defects, has expired, or has been brought offline, the system will notify you by SMS message or email and deliver an upgrade task during the maintenance window.

Precautions
-----------

-  The upgrade duration depends on how many nodes your database proxy has. Perform the upgrade during off-peak hours.
-  During the upgrade, short connections are not affected. Persistent connections lasting for more than 24 hours will be interrupted intermittently.
-  Only HA or cluster proxies can be upgraded.

Constraints
-----------

-  Only proxy instances with kernel version 2.3.0.1 or later can be upgraded manually on the console.
-  A version upgrade cannot be rolled back after the upgrade is complete.

.. _rds_11_0024__section9833938144:

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. On the **Database Proxy** page, in the **Proxy Instance Information** area, click **Upgrade** in the **Version** field.
#. In the displayed dialog box, select a scheduled time and click **OK**.

   -  Upon submission: The system upgrades the proxy instance to the latest version immediately after you submit the request. You can view the task progress in **Task Center** > **Instant Tasks**.
   -  In maintenance window: The system upgrades the proxy instance to the latest version during a maintenance window. You can view the task progress in **Task Center** > **Scheduled Tasks**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
