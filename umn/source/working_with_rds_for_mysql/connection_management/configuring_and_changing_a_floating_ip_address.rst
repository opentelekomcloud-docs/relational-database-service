:original_name: rds_05_0024.html

.. _rds_05_0024:

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

#. On the **Instances** page, click the target DB instance name to go to the **Overview** page.

#. Under **Floating IP Address**, click **Configure**.

#. In the displayed dialog box, check the number of in-use IP addresses. If the in-use IP addresses are less than 254, there are unused floating IP addresses.

#. Select an available IP address and click **OK**.

   An in-use IP address cannot be used as the new floating IP address of the DB instance.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
