:original_name: slow_query_log-pg.html

.. _slow_query_log-pg:

Viewing Slow Query Logs
=======================

**Scenarios**
-------------

Slow query logs record statements that exceed the **log_min_duration_statement** value. You can view log details to identify statements that are slowly executed and optimize the statements.

RDS supports the following statement types:

-  SELECT
-  INSERT
-  UPDATE
-  DELETE
-  CREATE
-  DROP
-  ALTER
-  DO
-  CALL
-  COPY

Parameter Description
---------------------

.. table:: **Table 1** Parameters related to PostgreSQL slow queries

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                               |
   +===================================+===========================================================================================================================================+
   | log_min_duration_statement        | Specifies how many milliseconds a query has to run before it has to be logged.                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | log_statement                     | Specifies the statement type. The value can be **none**, **ddl**, **mod**, or **all**.                                                    |
   |                                   |                                                                                                                                           |
   |                                   | The default value is **none**. If you change the value to **all**, the database log format changes and slow query logs fail to be parsed. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

Viewing Log Details
-------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Logs**. On the **Slow Query Logs** page, view details about slow query logs.

   -  You can view the slow query log records of a specified execution statement type or a specific time period.
   -  The **log_min_duration_statement** parameter determines when a slow query log is recorded. However, changes to this parameter do not affect already recorded logs. If **log_min_duration_statement** is changed from 1s to 0.1s, none of the previously recorded logs that do not meet the new threshold are deleted. For example, a 1.5s SQL statement that was recorded when the threshold was 1s will not be deleted now that the new threshold is 2s.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
