:original_name: rds_sqlserver_0025.html

.. _rds_sqlserver_0025:

Binding and Unbinding an EIP
============================

**Scenarios**
-------------

By default, a DB instance is not publicly accessible (not bound with an EIP) after being created. You can bind an EIP to a DB instance for public accessibility, and you can unbind the EIP from the DB instance later if needed.

.. important::

   To ensure that the DB instance is accessible, the security group associated with the instance must allow access over the database port. For example, if the database port is 8635, ensure that the security group allows access over the 8635 port.

Prerequisites
-------------

-  You have assigned an EIP on the VPC console.
-  You can bind an EIP to a primary DB instance or a read replica only.
-  If a DB instance has already been bound with an EIP, you must unbind the EIP from the DB instance first before binding a new EIP to it.

.. _rds_sqlserver_0025__en-us_topic_0192953725_section3199593620428:

Binding an EIP
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. On the **EIPs** page, click **Bind EIP**.

#. In the displayed dialog box, all unbound EIPs are listed. Select the EIP to be bound and click **OK**. If no available EIPs are displayed, click **View EIP** and obtain an EIP.

#. On the **EIPs** page of the RDS console, view the EIP that has been bound to the DB instance.

   You can also view the progress and result of binding an EIP to a DB instance on the **Task Center** page.

   To unbind the EIP from the DB instance, see :ref:`Unbinding an EIP <rds_sqlserver_0025__en-us_topic_0192953725_section186511510267>`.

.. _rds_sqlserver_0025__en-us_topic_0192953725_section186511510267:

Unbinding an EIP
----------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the DB instance that has an EIP bound.

#. On the **EIPs** page, locate the target EIP to be unbound and click **Unbind**. In the displayed dialog box, click **Yes**.

#. On the **EIPs** page, view the unbinding result.

   You can also view the progress and result of unbinding an EIP from a DB instance on the **Task Center** page.

   To bind an EIP to the DB instance again, see :ref:`Binding an EIP <rds_sqlserver_0025__en-us_topic_0192953725_section3199593620428>`.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001470260233.png
