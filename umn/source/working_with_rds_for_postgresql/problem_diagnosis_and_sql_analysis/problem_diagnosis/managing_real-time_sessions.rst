:original_name: rds_pg_08_0026.html

.. _rds_pg_08_0026:

Managing Real-Time Sessions
===========================

Scenarios
---------

You can query session snapshots of your instance while sorting, filtering, and displaying the snapshots as needed. You can also view session statistics by user, source, and database. Sessions can be killed for urgent instance recovery to ensure database availability.

Precautions
-----------

Killing a session may cause the application to disconnect from the instance. Your application should be able to reconnect to the instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target instance name.
#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.
#. Click the **Sessions** tab. You can perform the following operations on this tab page:

   -  Viewing session statistics

      In the session statistics area, you can view the session summary and session statistics by user, source, and database.

   -  Killing abnormal sessions

      In the session list, select the abnormal session you want to end and click **Kill Session** to recover the database.

   -  Exporting the session list

      To export the session list, click |image2| above it.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000002390290289.png
