:original_name: rds_mysql_slow_query_log.html

.. _rds_mysql_slow_query_log:

Viewing Slow Query Logs
=======================

**Scenarios**
-------------

Slow query logs record statements that exceed **long_query_time**. You can use these logs to identify and optimize the statements that are executing slowly.

RDS supports the following statement types:

-  SELECT
-  INSERT
-  UPDATE
-  DELETE
-  CREATE

Viewing Log Details
-------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Logs**. On the **Slow Query Logs** page, view details about slow query logs.

   -  You can view the slow query log records of a specified execution statement type or a specific time period.
   -  The **long_query_time** parameter determines when a slow query log is recorded. However, changes to this parameter do not affect already recorded logs. If **long_query_time** is changed from 1s to 0.1s, none of the previously recorded logs that do not meet the new threshold are deleted. For example, a 1.5s SQL statement that was recorded when the threshold was 1s will not be deleted now that the new threshold is 2s.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
