:original_name: en-us_topic_scale_rds.html

.. _en-us_topic_scale_rds:

Changing a DB Instance Class
============================

Scenarios
---------

You can change the instance class (CPU or memory) of a DB instance as required. If the status of a DB instance changes from **Changing instance class** to **Available**, the change is successful.

Constraints
-----------

-  A DB instance cannot be deleted when its instance class is being changed.
-  After you change instance classes, the DB instances will be rebooted and service will be interrupted. Therefore, you are advised to change instance classes during off-peak hours.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Change Instance Class** in the **Operation** column.

   Alternatively, click the target DB instance to go to the **Basic Information** page. In the **DB Information** area, click **Change** in the **Instance Class** field.

#. On the displayed page, specify the new instance class and click **Next**.

#. View the DB instance class change result.

   Changing the DB instance class takes 5-15 minutes. During this period, the status of the DB instance on the **Instances** page is **Changing instance class**. After a few minutes, click the DB instance and view the instance class on the displayed **Basic Information** page to check that the change is successful.

   .. important::

      After you change a MySQL instance class, the values of the following parameters will also be changed accordingly: **back_log**, **innodb_buffer_pool_size**, **innodb_log_buffer_size**, **innodb_log_files_in_group**, **max_connections**, **innodb_page_cleaners**, **innodb_buffer_pool_instances**, **threadpool_size**, and **slave_parallel_workers**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
