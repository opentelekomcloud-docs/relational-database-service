:original_name: rds_11_0019.html

.. _rds_11_0019:

Disabling Read/Write Splitting
==============================

You can disable read/write splitting as required.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance. The **Basic Information** page is displayed.
#. In the navigation pane on the left, choose **Database Proxy**.
#. In the proxy instance area, click **Delete Proxy**. In the displayed dialog box, click **OK**.

   .. note::

      -  If the database proxy is disabled, read/write splitting is also disabled and services using the read/write splitting address are interrupted. You need to switch your applications to the instance address.
      -  After read/write splitting is disabled, read replicas are still be billed. You can release them if they are not required for your workloads anymore.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
