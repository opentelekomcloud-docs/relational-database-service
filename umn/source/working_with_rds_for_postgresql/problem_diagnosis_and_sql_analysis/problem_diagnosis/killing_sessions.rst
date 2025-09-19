:original_name: rds_pg_08_0039.html

.. _rds_pg_08_0039:

Killing Sessions
================

Scenarios
---------

You can kill sessions when necessary on the **Sessions that Can Be Killed If Necessary** tab page. This page covers:

-  **Emergency Channel**: If the maximum number of connections for an instance has been reached and the instance cannot be logged in to, you can view and kill unnecessary sessions through this channel.
-  **History Logs**: You can view history logs to learn details of the kill operations that you performed using the emergency channel.

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
#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.
#. Choose **Sessions** > **Sessions that Can Be Killed If Necessary**.

   -  To kill a session, click the **Emergency Channel** tab, select the session, and click **Kill Session**.
   -  To check the kill history, click the **History Logs** tab.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
