:original_name: rds_faq_0100.html

.. _rds_faq_0100:

What Should I Do If an RDS Microsoft SQL Server DB Instance Failed to Be Connected?
===================================================================================

Fault Location
--------------

-  Check whether the ECS can connect to the RDS DB instance.

   If the ECS cannot connect to the RDS DB instance, check whether the ECS and RDS DB instance are located in the same VPC and security group.

   In private network connection mode, the ECS and RDS DB instance must be in the same VPC and the DB instance can be accessed only through an ECS in the same VPC. In public network connection mode, the ECS and DB instance can be in different VPCs.

-  Check whether the IP address and port are correct.

   Use a colon to separate the IP address and port.

-  Check whether the RDS service is running properly.

-  Check whether the username and password are correct. You can reset the password.

-  Reboot the RDS DB instance and check whether it can be connected through an ECS.

Solution
--------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance. On the **Basic Information** and **Backups & Restorations** pages, check connection and backup information.
#. On the **Basic Information** page, check the administrator.
#. Download an SQL Server Management Studio installation package and install it on an ECS.
#. Connect to the RDS DB instance through an ECS.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
