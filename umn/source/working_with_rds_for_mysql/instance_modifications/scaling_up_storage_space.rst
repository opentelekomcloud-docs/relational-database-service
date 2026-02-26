:original_name: en-us_topic_scale_cluster.html

.. _en-us_topic_scale_cluster:

Scaling up Storage Space
========================

Scenarios
---------

If the original storage space is insufficient as your services grow, scale up storage space of your DB instance.

You are advised to set alarm rules for the storage space usage by referring to :ref:`Setting Alarm Rules <rds_06_0002>`.

RDS allows you to scale up storage space of DB instances but you cannot change the storage type. During the scale-up period, services are not interrupted.

Instance Becomes Read-Only When Storage Is Full
-----------------------------------------------

For details about the causes and solutions of insufficient storage space, see :ref:`What Should I Do If My Data Exceeds the Available Storage of an RDS DB Instance? <rds_faq_0046>`

.. table:: **Table 1** Conditions under which an instance becomes read-only if it is out of storage

   +------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | Storage Size                                   | Condition                                                                                                     |
   +================================================+===============================================================================================================+
   | Any storage size                               | If the available storage space is less than 5 GB, the instance becomes read-only.                             |
   |                                                |                                                                                                               |
   |                                                | .. note::                                                                                                     |
   |                                                |                                                                                                               |
   |                                                |    This rule takes precedence over other rules that can be used to set the instance read-only.                |
   +------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | Storage size is less than 1 TB.                | -  If the storage usage reaches 97%, the instance becomes read-only.                                          |
   |                                                | -  If the storage usage decreases to 87%, the instance exits the read-only state.                             |
   +------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | Storage size is greater than or equal to 1 TB. | -  If the available storage space is less than 30 GB, the instance becomes read-only.                         |
   |                                                | -  If the available storage space is greater than or equal to 150 GB, the instance exits the read-only state. |
   +------------------------------------------------+---------------------------------------------------------------------------------------------------------------+

Constraints
-----------

-  The maximum allowed storage is 4,000 GB. There is no limit on the number of scale-ups.
-  The DB instance is in **Scaling up** state when its storage space is being scaled up and the backup services are not affected.
-  For primary/standby DB instances, scaling up the primary DB instance will cause the standby DB instance to also be scaled up accordingly.
-  You cannot reboot or delete a DB instance that is being scaled up.
-  Storage space can only be scaled up, not down.
-  If you scale up a DB instance with disks encrypted, the expanded storage space will be encrypted using the original encryption key.

Scaling up a Primary DB Instance
--------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Scale Storage Space** in the **Operation** column.

   You can also perform the following operations to scale up storage space:

   -  Click the target DB instance to enter the **Overview** page. In the **Storage & Backup** area, click **Scale Storage Space**.

#. On the displayed page, specify the new storage space and click **Next**.

   The minimum increment for each scaling is 10 GB.

#. Confirm specifications.

   -  If you need to modify your settings, click **Previous**.
   -  If you do not need to modify your settings, click **Submit**.

#. View the scale-up result.

   Scaling up storage space takes 3-5 minutes. During the time period, the status of the DB instance on the **Instances** page will be **Scaling up**. Click the DB instance and view the utilization on the displayed **Overview** page to verify that the scale-up is successful.

   If the DB instance is running the MySQL DB engine, you can view the detailed progress and result of the task on the **Task Center** page. For details, see section :ref:`Task Center <rds_05_0007>`.

Scaling up a Read Replica
-------------------------

Scaling up the storage space of a read replica does not affect that of the primary DB instance. Therefore, you can separately scale read replicas to meet service requirements. New storage space of read replicas after scaling up must be greater than or equal to that of the primary DB instance.

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and click |image3| in front of it. Locate a read replica to be scaled and choose **More** > **Scale Storage Space** in the **Operation** column.

   You can also perform the following operations to scale up storage space:

   -  Click the target DB instance to enter the **Overview** page. In the **Storage & Backup** area, click **Scale Storage Space**.

#. On the displayed page, specify the new storage space and click **Next**.

   The minimum increment for each scaling is 10 GB.

#. Confirm specifications.

   -  If you need to modify your settings, click **Previous**.
   -  If you do not need to modify your settings, click **Submit**.

#. View the scale-up result.

   Scaling up storage space takes 3-5 minutes. During the time period, the status of the read replica on the **Instances** page will be **Scaling up**. Click the read replica and view the utilization on the displayed **Overview** page to verify that the scale-up is successful.

   If the read replica is running the MySQL DB engine, you can view the detailed progress and result of the task on the **Task Center** page. For details, see section :ref:`Task Center <rds_05_0007>`.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211679.png
.. |image3| image:: /_static/images/en-us_image_0000002459797326.png
