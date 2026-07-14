:original_name: rds_task_pg_0001.html

.. _rds_task_pg_0001:

Viewing a Task
==============

You can view the detailed progress and result of the task on the **Task Center** page.

Supported Tasks
---------------

.. table:: **Table 1** Supported tasks

   +-----------------------------------+-----------------------------------------------------------------------------------+
   | Category                          | Task Name                                                                         |
   +===================================+===================================================================================+
   | Instance creation                 | Creating a PostgreSQL DB instance                                                 |
   |                                   |                                                                                   |
   |                                   | Creating a PostgreSQL read replica                                                |
   |                                   |                                                                                   |
   |                                   | Creating a PostgreSQL read replica from a snapshot                                |
   +-----------------------------------+-----------------------------------------------------------------------------------+
   | Instance lifecycle                | Rebooting a PostgreSQL DB instance                                                |
   |                                   |                                                                                   |
   |                                   | Stop PostgreSQL instance                                                          |
   |                                   |                                                                                   |
   |                                   | Delete PostgreSQL instance                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------+
   | Instance modifications            | Applying for a PostgreSQL private domain name                                     |
   |                                   |                                                                                   |
   |                                   | Changing a PostgreSQL private domain name                                         |
   |                                   |                                                                                   |
   |                                   | Forcing a PostgreSQL instance failover                                            |
   |                                   |                                                                                   |
   |                                   | Switching PostgreSQL primary/standby DB instances                                 |
   |                                   |                                                                                   |
   |                                   | Changing a PostgreSQL DB instance class                                           |
   |                                   |                                                                                   |
   |                                   | PostgreSQL instance disk encryption                                               |
   |                                   |                                                                                   |
   |                                   | Changing the PostgreSQL instance type from single to primary/standby              |
   |                                   |                                                                                   |
   |                                   | Scaling a PostgreSQL DB instance                                                  |
   |                                   |                                                                                   |
   |                                   | Enabling public accessibility for a PostgreSQL DB instance                        |
   |                                   |                                                                                   |
   |                                   | Disabling public accessibility for a PostgreSQL DB instance                       |
   +-----------------------------------+-----------------------------------------------------------------------------------+
   | Version upgrade                   | PostgreSQL major version upgrade                                                  |
   |                                   |                                                                                   |
   |                                   | PostgreSQL instance version upgrade                                               |
   +-----------------------------------+-----------------------------------------------------------------------------------+
   | Backup and restoration            | Restoring to a new PostgreSQL DB instance                                         |
   |                                   |                                                                                   |
   |                                   | Restoring PostgreSQL data to an existing instance                                 |
   |                                   |                                                                                   |
   |                                   | RDS for PostgreSQL table-level restoration                                        |
   |                                   |                                                                                   |
   |                                   | RDS for PostgreSQL database-level restoration                                     |
   |                                   |                                                                                   |
   |                                   | Restoring data from a PostgreSQL read replica with delayed replication to primary |
   +-----------------------------------+-----------------------------------------------------------------------------------+
   | Parameter configuration           | PostgreSQL parameter template modification                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------+

Viewing an Instant Task
-----------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. Choose **Task Center** in the navigation pane on the left. Locate the target task and view its details on the displayed **Instant Tasks** page.

   -  To identify the target task, you can use the task name, order ID, or DB instance name/ID, or simply enter the target task name in the search box in the upper right corner.

   -  You can view the progress and status of tasks in a specific period. The default period is seven days.

      The task list shows tasks that have been executed in the past 30 days.

   -  You can view instant tasks in the following statuses:

      -  Running
      -  Completed
      -  Failed

   -  You can view the task creation and completion time.

Viewing a Scheduled Task
------------------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. Choose **Task Center** in the navigation pane on the left. On the **Scheduled Tasks** page, view the task progress and results.

   -  To identify the target task, you can use the DB instance name/ID or enter the target DB instance ID in the search box in the upper right corner.
   -  You can view the scheduled tasks in the following statuses:

      -  Running
      -  Completed
      -  Failed
      -  Canceled
      -  To be executed
      -  To be authorized

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211679.png
