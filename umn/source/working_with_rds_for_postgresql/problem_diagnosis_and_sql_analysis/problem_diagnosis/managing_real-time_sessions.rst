:original_name: rds_pg_08_0026.html

.. _rds_pg_08_0026:

Managing Real-Time Sessions
===========================

Scenarios
---------

You can query session snapshots of your instance while sorting, filtering, and displaying the snapshots as needed. You can also view session statistics by user, source, and database.

Sessions can be killed for urgent instance recovery to ensure database availability. If the maximum number of connections for an instance has been reached and the instance cannot be logged in to, you can view and kill unnecessary sessions.

Precautions
-----------

Killing a session may cause the application to disconnect from the instance. Your application should be able to reconnect to the instance.

Constraints
-----------

-  Do not kill sessions unless you really need to. All your kill operations will be logged.
-  Sessions of sensitive users such rdsAdmin, rdsBackup, rdsMetric, and rdsRepl, and sessions whose username is null cannot be killed.
-  You may fail to refresh the session list if your instance has a heavy load. Minimize the resources occupied by the emergency channel. Wait a few seconds and try again.
-  If the CPU usage reaches 100%, requests to kill sessions may fail. You may have to try more than once.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target instance name.
#. In the navigation pane, choose **Sessions** under **DBA Assistant**.
#. Click the **Sessions** page. You can perform the following operations on this tab page:

   -  Viewing session statistics

      In the session statistics area, you can view the session summary and session statistics by user, source, and database.

   -  Killing abnormal sessions

      In the session list, select the abnormal session you want to end and click **Kill Session** to recover the database.

   -  Viewing the CPU/memory usage of databases

      In the session list, click **Statistics By Database** to view the CPU/memory usage of databases in the instance.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
