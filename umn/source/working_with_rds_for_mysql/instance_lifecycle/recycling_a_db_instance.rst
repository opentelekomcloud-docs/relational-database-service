:original_name: rds_mysql_recycle.html

.. _rds_mysql_recycle:

Recycling a DB Instance
=======================

Scenarios
---------

Deleted DB instances can be moved to the recycle bin. You can rebuild DB instances from the recycle bin. The DB engine, DB engine version, and storage type of the new DB instance are the same as those of the original DB instance. Other parameters can be reconfigured. DB instances that were deleted up to 7 days ago can be restored.

Constraints
-----------

-  Read replicas cannot be moved to the recycle bin.
-  The recycle bin is enabled by default and cannot be disabled.

Modifying Recycling Policy
--------------------------

.. important::

   A new recycling policy only applies to DB instances that were put in the recycle bin after the new policy was put into effect. For DB instances that were in the recycle bin before the modification, the original recycling policy takes effect.

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. In the navigation pane on the left, choose **Recycling Management**.
#. On the **Recycling Management** page, click **Modify Recycling Policy**. In the displayed dialog box, set the retention period for the deleted DB instances from 1 day to 7 days.
#. Then, click **OK**.

Rebuilding a DB Instance
------------------------

You can rebuild the primary DB instances in the recycle bin within the retention period.

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. In the navigation pane on the left, choose **Recycling Management**.
#. On the **Recycling Management** page, locate the target DB instance to be rebuilt and click **Rebuild** in the **Operation** column.
#. On the **Rebuild DB Instance** page, configure required information and submit the rebuild task. For details, see :ref:`Restoring from Backup Files to DB Instances <rds_08_0007>`.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001470260233.png
