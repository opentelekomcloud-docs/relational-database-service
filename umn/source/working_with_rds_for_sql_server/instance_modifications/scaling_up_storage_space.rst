:original_name: rds_sqlserver_scale_cluster.html

.. _rds_sqlserver_scale_cluster:

Scaling up Storage Space
========================

Scenarios
---------

If the original storage space is insufficient as your services grow, scale up storage space of your DB instance.

The DB instance needs to preserve at least 15% of its capacity to work properly. The new minimum storage space required to make this instance available has been automatically calculated for you. You are advised to set alarm rules for the storage space usage by referring to :ref:`Setting Alarm Rules <rds_sqlserver_06_0002>`.

For details about the causes and solutions of insufficient storage space, see :ref:`What Should I Do If My Data Exceeds the Available Storage of an RDS DB Instance? <rds_faq_0046>`

RDS allows you to scale up storage space of DB instances but you cannot change the storage type. During the scale-up period, services are not interrupted.

Constraints
-----------

-  DB instances can be scaled up numerous times.
-  The maximum allowed storage is 4,000 GB. There is no limit on the number of scale-ups.
-  For primary/standby DB instances, scaling up the primary DB instance will cause the standby DB instance to also be scaled up accordingly.
-  You cannot reboot or delete a DB instance that is being scaled up.
-  Storage space can only be scaled up.
-  If you scale up a DB instance with disks encrypted, the expanded storage space will be encrypted using the original encryption key.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Scale Storage Space** in the **Operation** column.

   You can also perform the following operations to scale up storage space:

   -  Click the target DB instance to enter the **Basic Information** page. In the **Storage Space** area, click **Scale**.

#. On the displayed page, specify the new storage space and click **Next**.

   The minimum start value of each scaling is 10 GB. A DB instance can be scaled up only by a multiple of 10 GB. The allowed maximum storage space is 4,000 GB.

#. Confirm specifications.

   -  If you need to modify your settings, click **Previous**.
   -  If you do not need to modify your settings, click **Submit**.

#. View the scale-up result.

   Scaling up storage space takes 3-5 minutes. During this time, the status of the DB instance on the **Instances** page will be **Scaling up**. Click the DB instance and view the utilization on the displayed **Basic Information** page to verify that the scale-up is successful.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
