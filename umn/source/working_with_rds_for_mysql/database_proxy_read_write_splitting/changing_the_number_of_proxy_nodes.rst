:original_name: rds_11_0045.html

.. _rds_11_0045:

Changing the Number of Proxy Nodes
==================================

Scenarios
---------

After read/write splitting is enabled, you can change the number of proxy nodes as required.

Prerequisites
-------------

-  Read/write splitting has been enabled.
-  The primary DB instance, read replicas, and proxy instance are all available.

Constraints
-----------

The number of proxy nodes ranges from 2 to 8.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the instance name.
#. In the **Proxy Instance Information** area on the **Database Proxy** page, click **Change** next to the **Proxy Nodes** field.
#. Set the number of proxy nodes and click **Next**.
#. Confirm the settings and click **Submit**.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
