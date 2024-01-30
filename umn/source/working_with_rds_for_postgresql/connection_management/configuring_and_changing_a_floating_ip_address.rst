:original_name: rds_pg_05_0024.html

.. _rds_pg_05_0024:

Configuring and Changing a Floating IP Address
==============================================

Scenarios
---------

You can change floating IP addresses after migrating on-premises databases or other cloud databases to RDS.

Constraints
-----------

After a floating IP address is changed, the domain name needs to be resolved again. This operation takes several minutes and may interrupt database connections. Therefore, you are advised to change a floating IP address during off-peak hours.

Configuring a Floating IP Address
---------------------------------

You can use an automatically-assigned IP address when creating a DB instance.

Changing a Floating IP Address
------------------------------

You can change the floating IP address of an existing DB instance.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the **Connection Information** area on the **Basic Information** page, click **Change** in the **Floating IP Address** field.

#. In the displayed dialog box, enter a new floating IP address and click **OK**.

   In the in-use IP address list, the IP addresses whose statuses are **To be used** are occupied and cannot be used.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
