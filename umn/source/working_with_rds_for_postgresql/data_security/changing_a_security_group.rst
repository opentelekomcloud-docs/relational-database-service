:original_name: rds_09_0026.html

.. _rds_09_0026:

Changing a Security Group
=========================

Scenarios
---------

This section describes how to change the security group of a primary DB instance or read replica. For primary/standby DB instances, changing the security group of the primary DB instance will cause the security group of the standby DB instance to also be changed accordingly.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target primary DB instance or read replica.
#. On the **Overview** page, click **Configure** under **Security Group**.
#. In the displayed dialog box, select one from the drop-down list.
#. Click **OK** to submit the modification.
#. Changing the security group takes 1 to 3 minutes. Click |image2| in the upper right corner on the **Overview** page to view the results.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001145051618.png
