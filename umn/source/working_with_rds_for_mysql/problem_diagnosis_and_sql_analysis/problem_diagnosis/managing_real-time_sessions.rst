:original_name: rds_08_0026.html

.. _rds_08_0026:

Managing Real-Time Sessions
===========================

Scenarios
---------

You can view current session statistics of your instance, identify abnormal sessions, and kill the sessions.

Setting Slow Session Threshold
------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the DB instance name.
#. In the navigation pane, choose **DBA Assistant** > **Real-Time Diagnosis**.
#. Click the **Sessions** tab. You can perform the following operations on this tab page:

   -  Viewing session statistics

      In the sessions statistics, you can view statistics on the slow sessions, active sessions, total sessions, long transaction sessions by user, access host, and database.

   -  Setting a slow session threshold

      Click |image2| next to the **Slow Session Threshold** field. In the displayed dialog box, set a slow session threshold and click **OK**. Sessions whose execution durations are greater than this threshold are automatically displayed.

   -  Killing abnormal sessions

      In the session list, you can view session details. You can also select the abnormal session you want to end and click **Kill Session** to recover the database.

      A maximum of 100 sessions can be killed at a time.

   -  Configuring SQL throttling

      In the session list, click **SQL Throttling** and set the SQL type and keyword to match SQL statements. When the number of matched SQL statements exceeds the configured upper limit, the DB instance will refuse to execute the SQL statements, thus ensuring the instance stability.

      For details, see :ref:`Creating a SQL Throttling Rule <rds_08_0033>`.

   -  Creating lock analysis

      To create a lock analysis task, log in to the DB instance on the **Locks & Transactions** page first. For details, see :ref:`Managing Locks & Transactions <rds_08_0029>`. Then, click **Create Lock Analysis**. A lock analysis record is generated, which is used to check whether there are any sessions that hold locks.

   -  Exporting the session list

      Click **Export** to export all or specified sessions.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000002422550952.png
