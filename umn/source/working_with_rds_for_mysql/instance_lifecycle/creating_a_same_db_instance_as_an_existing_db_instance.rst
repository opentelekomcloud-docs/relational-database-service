:original_name: rds_05_0055.html

.. _rds_05_0055:

Creating a Same DB Instance as an Existing DB Instance
======================================================

Scenarios
---------

This section describes how to quickly create a DB instance with the same configurations as the selected one.

.. note::

   -  You can create DB instances with the same configurations numerous times.
   -  This function is unavailable for read replicas.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Create** **Same DB Instance** in the **Operation** column.

#. On the displayed page, the configurations are the same as those of the selected DB instance. You can change them as required. Then, click **Create Now**.

   For details about MySQL DB instance configurations, see section :ref:`Step 1: Create a DB Instance <rds_02_0008>`.

#. Confirm the instance specifications.

#. Refresh the DB instance list and view the status of the DB instance. If the status is **Available**, it has been created successfully.

   You can manage the DB instance on the **Instances** page.

.. |image1| image:: /_static/images/en-us_image_0000001744574182.png
