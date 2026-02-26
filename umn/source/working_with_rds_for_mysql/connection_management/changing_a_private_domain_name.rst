:original_name: rds_05_0085.html

.. _rds_05_0085:

Changing a Private Domain Name
==============================

You can connect to RDS DB instances through private domain names.

Constraints
-----------

-  Changing the private domain name will interrupt your database connection. To reconnect to the instance, change the connection address of your applications. The new private domain name is applied to the instance about 5 minutes after the change.
-  If your DB instance is connected through a private domain name, changing its floating IP address does not interrupt services.

Procedure
---------

When you buy a DB instance, the system automatically assigns a private domain name to your instance.

After the DB instance is created, you can change the private domain name as needed.

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance name to go to the **Overview** page.

#. Under **Private Domain Name**, click **Configure**.

   Alternatively, in the navigation pane on the left, choose **Connectivity & Security**. On the displayed page, click **Change** next to the **Private Domain Name** field.

#. In the displayed dialog box, enter a new domain name and click **OK**.

   -  Only the prefix of a private domain name can be modified.
   -  The prefix of a private domain name contains 8 to 63 characters, and can include only letters and digits.
   -  The new private domain name must be different from existing ones.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
