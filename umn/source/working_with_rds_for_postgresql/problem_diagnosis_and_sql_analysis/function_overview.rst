:original_name: rds_pg_08_0037.html

.. _rds_pg_08_0037:

Function Overview
=================

DBA Assistant provides visualized database O&M and intelligent diagnosis for developers and database administrators (DBAs), making database O&M easy and efficient. By analyzing alarms, resources, and performance metrics, it helps users quickly locate faults and keep track of instance status.

Scenarios
---------

-  In emergency cases, you can manually terminate slow sessions to recover your instance, improving database availability.
-  If your DB instance is unstable due to a large number of concurrent SQL requests from new services, you can set SQL throttling rules for SQL statements to limit concurrent SQL statements and ensure instance stability.

Functions
---------

:ref:`Table 1 <rds_pg_08_0037__table3237102219912>` lists the functions supported by DBA Assistant.

.. _rds_pg_08_0037__table3237102219912:

.. table:: **Table 1** Function description

   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Function         | Description                                                                                                                                                                                                                                                                 | Reference                                                            |
   +==================+=============================================================================================================================================================================================================================================================================+======================================================================+
   | Performance      | Displays key metrics of your instance and provides metric comparison between different days. You can keep track of metric changes and detect exceptions in a timely manner.                                                                                                 | :ref:`Viewing Performance Metrics of a DB Instance <rds_pg_08_0027>` |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Killing Sessions | If the maximum number of connections for an instance has been reached and the instance cannot be logged in to, you can view and kill unnecessary sessions through the emergency channel.                                                                                    | :ref:`Killing Sessions <rds_pg_08_0039>`                             |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Sessions         | You can query session snapshots of your instance while sorting, filtering, and displaying the snapshots as needed. You can also view session statistics by user, source, and database. Sessions can be killed for urgent instance recovery to ensure database availability. | :ref:`Managing Real-Time Sessions <rds_pg_08_0026>`                  |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Slow Query Log   | Displays slow queries within a specified time period. You can view top 5 slow query logs by user or client IP address, sort statistics, and identify sources of slow SQL statements.                                                                                        | :ref:`Viewing Slow Query Logs of a DB Instance <rds_pg_08_0030>`     |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | SQL Insights     | After **Collect All SQL Statements** is enabled, you can gain a comprehensive insight into SQL statements on the **SQL Explorer** page. Top SQL helps you locate exceptions.                                                                                                | :ref:`Creating a SQL Insights Task <rds_pg_08_0032>`                 |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | SQL Throttling   | SQL Throttling restricts the execution of SQL statements based on specified rules when there are SQL statements that cannot be optimized timely or a resource (for example, vCPU) bottleneck occurs.                                                                        | :ref:`Creating a SQL Throttling Rule <rds_pg_08_0033>`               |
   +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
