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
#. In the **Connection Information** area on the **Basic Information** page, click |image2| in the **Security Group** field.

   -  To submit the change, click |image3|.
   -  To cancel the change, click |image4|.

#. Changing the security group takes 1 to 3 minutes. Click |image5| in the upper right corner on the **Basic Information** page to view the results.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
.. |image2| image:: /_static/images/en-us_image_0000001739973860.png
.. |image3| image:: /_static/images/en-us_image_0000001739973952.png
.. |image4| image:: /_static/images/en-us_image_0000001786854037.png
.. |image5| image:: /_static/images/en-us_image_0000001786933873.png
