:original_name: rds_11_0028.html

.. _rds_11_0028:

Changing the Instance Class of a DB Proxy Instance
==================================================

Scenarios
---------

You can change the instance class (vCPU or memory) of a DB proxy instance as required. If the DB instance status changes from **Changing proxy instance class** to **Available**, the change was successful.

Constraints
-----------

-  You can change the instance class of a DB proxy instance only when the statuses of your primary DB instance, read replicas, and DB proxy instance are **Available**.
-  A DB proxy instance cannot be deleted when its instance class is being changed.
-  Changing the instance class of a DB proxy instance will cause the instance to reboot. Therefore, perform the operation during off-peak hours.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the instance name.

#. Choose **Database Proxy** from the navigation pane on the left. In the **Proxy Instance Information** area, click **Change** in the **Specifications** field.

   You can change the DB proxy instance class if required.

   Changing the DB proxy instance class will cause the instance to reboot. To prevent service interruptions, change the DB proxy instance class during off-peak hours.

   If you have selected **Maintenance Window** for **Scheduled Time**, the DB proxy instance will be rebooted during the instance class change time and services will be interrupted. To prevent service interruptions, you are advised to set the maintenance window to off-peak hours. For details, see :ref:`Changing the Maintenance Window <rds_05_0038>`.

#. Confirm the specifications and click **Submit**.

   If you need to modify your settings, click **Previous**.

#. View the instance class change result.

   Changing the DB proxy instance class takes 13-15 minutes. During this period, the status of the primary DB instance on the **Instances** page is **Changing proxy instance class**. After a few minutes, view the proxy instance class on the **Database Proxy** page to check that the change is successful.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
