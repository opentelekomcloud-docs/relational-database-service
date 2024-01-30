:original_name: rds_11_0024.html

.. _rds_11_0024:

Upgrading the Kernel Version of Database Proxy
==============================================

Scenarios
---------

You can manually upgrade the RDS for MySQL database proxy to the latest kernel version to improve performance, add new functions, and fix problems.

Precautions
-----------

Intermittent disconnections occur during the upgrade. The time required to complete the upgrade depends on how many proxy instances there are. Perform the upgrade during off-peak hours.

Constraints
-----------

-  Only proxy instances with kernel version 2.3.0.1 or later can be upgraded manually on the console.
-  A version upgrade cannot be rolled back after the upgrade is complete.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. On the **Database Proxy** page, in the **Proxy Instance Information** area, click **Upgrade** in the **Version** field.
#. In the displayed dialog box, select a scheduled time and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
