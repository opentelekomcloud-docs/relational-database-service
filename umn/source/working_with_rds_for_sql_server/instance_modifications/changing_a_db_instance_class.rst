:original_name: rds_sqlserver_scale_rds.html

.. _rds_sqlserver_scale_rds:

Changing a DB Instance Class
============================

Scenarios
---------

You can change the instance class (CPU or memory) of a DB instance as required. If the status of a DB instance changes from **Changing instance class** to **Available**, the change is successful.

Constraints
-----------

-  You can change the DB instance class or the DB instance storage.
-  A DB instance cannot be deleted when its instance class is being changed.

-  After you change instance classes, the DB instances will be rebooted and service will be interrupted. Therefore, you are advised to change instance classes during off-peak hours.
-  Set the recovery model of your database to FULL instead of SIMPLE.

   -  In the SIMPLE recovery model, no incremental backup is performed for the database, so the database cannot be restored to a specified time point.
   -  For primary/standby or cluster instances, if the recovery model is set to SIMPLE, no replication relationship will be established for the instances. As a result, a primary/standby switchover or instance class change cannot be performed.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Change Instance Class** in the **Operation** column.

   Alternatively, click the target DB instance to go to the **Overview** page. Under **Instance Class**, click **Configure**.

#. On the displayed page, specify the new instance class and click **Next**.

#. View the DB instance class change result.

   Changing the DB instance class takes 5-15 minutes. During this period, the status of the DB instance on the **Instances** page is **Changing instance class**. After a few minutes, click the DB instance and view the instance class on the displayed **Overview** page to check that the change is successful.

   .. important::

      After you change a Microsoft SQL Server DB instance class, the value of **max server memory** will also be changed accordingly. You are advised to set it to a size equal to the memory size minus 520 MB. For example, if there is 1 GB of memory (1,024 MB), you are advised to set **max server memory** to 504 MB (1,024 MB - 520 MB).

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
