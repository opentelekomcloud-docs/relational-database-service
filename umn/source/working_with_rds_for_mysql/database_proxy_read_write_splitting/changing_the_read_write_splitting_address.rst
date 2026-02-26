:original_name: rds_11_0026.html

.. _rds_11_0026:

Changing the Read/Write Splitting Address
=========================================

Scenarios
---------

After read/write splitting is enabled, you can change the read/write splitting address.

Precautions
-----------

Changing the read/write splitting address will interrupt database connections and services. Therefore, change the read/write splitting address during off-peak hours or when services are stopped.

Constraints
-----------

The new IP address is not in use and must be in the same subnet as the RDS for MySQL instance.

Procedure
---------

You can change the read/write splitting address for DB instances with read/write splitting enabled.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the **Connectivity** area on the **Overview** page, click **Modify** next to the **Read/Write Splitting Address** field.

   Alternatively, click **Database Proxy** in the navigation pane on the left. On the displayed page, click **Modify** next to the **Read/Write Splitting Address** field.

#. In the displayed dialog box, enter a new address. Click **OK**.

   In-use IP addresses cannot be used as read/write splitting addresses.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
