:original_name: rds_pg_public_accessibility.html

.. _rds_pg_public_accessibility:

Binding and Unbinding an EIP
============================

**Scenarios**
-------------

By default, a DB instance is not publicly accessible (not bound with an EIP) after being created. You can bind an EIP to a DB instance for public accessibility, and you can unbind the EIP from the DB instance later if needed.

.. important::

   To ensure that the DB instance is accessible, the security group associated with the instance must allow access over the database port. For example, if the database port is 5432, ensure that the security group allows access over the 5432 port.

Prerequisites
-------------

-  You have assigned an EIP on the VPC console.
-  You can bind an EIP to a primary DB instance or a read replica only.
-  If a DB instance has already been bound with an EIP, you must unbind the EIP from the DB instance first before binding a new EIP to it.

Binding an EIP
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Connectivity & Security**. In the **Connection Information** area, click **Bind** next to the **EIP** field.

#. In the displayed dialog box, all unbound EIPs are listed. Select the EIP to be bound and click **OK**. If no available EIPs are displayed, click **View EIP** to obtain an EIP.

#. On the **Connectivity & Security** page, check the EIP that has been bound to the DB instance.

   You can also view the progress and result of binding an EIP to a DB instance on the **Task Center** page.

Unbinding an EIP
----------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the DB instance that has an EIP bound.

#. In the navigation pane on the left, choose **Connectivity & Security**. In the **Connection Information** area, click **Unbind** next to the **EIP** field.

#. In the displayed dialog box, click **OK**.

#. On the **Connectivity & Security** page, check the results.

   You can also view the progress and result of unbinding an EIP from a DB instance on the **Task Center** page.

.. |image1| image:: /_static/images/en-us_image_0000002492743401.png
.. |image2| image:: /_static/images/en-us_image_0000002492863365.png
