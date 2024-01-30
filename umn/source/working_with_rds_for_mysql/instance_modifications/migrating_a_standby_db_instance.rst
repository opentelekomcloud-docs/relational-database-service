:original_name: rds_05_0060.html

.. _rds_05_0060:

Migrating a Standby DB Instance
===============================

Scenarios
---------

You can migrate a standby DB instance to another AZ in the same region as the original AZ.

.. note::

   -  Primary/standby instances running MySQL 5.6, 5.7, or 8.0 support standby instance migration to another AZ.
   -  DDL operations and scheduled events will be suspended during migration. To prevent service interruptions, perform the migration during off-peak hours.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, locate the target DB instance and choose **More** > **Migrate Standby DB Instance** in the **Operation** column.
#. On the displayed page, select a target AZ and click **Submit**.
#. After the migration is complete, you can view and manage the DB instance on the **Instances** page.

   -  During the migration process, the DB instance status is **Migrating standby DB instance**. You can view the progress on the **Task Center** page. For details, see section :ref:`Task Center <rds_05_0007>`.
   -  In the upper right corner of the DB instance list, click |image2| to refresh the list. After the migration is complete, the DB instance status will become **Available**.
   -  In the **DB Information** on the **Basic Information** page, you can view the AZ hosting the standby DB instance.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
.. |image2| image:: /_static/images/en-us_image_0000001739814972.png
