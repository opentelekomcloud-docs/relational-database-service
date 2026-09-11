:original_name: rds_task_0001.html

.. _rds_task_0001:

Viewing a Task
==============

You can view the progress and results of scheduled and instant tasks on the **Task Center** page.

Supported Tasks
---------------

.. table:: **Table 1** Supported tasks

   +-----------------------------------+-----------------------------------------------------------------+
   | Category                          | Task Name                                                       |
   +===================================+=================================================================+
   | Instance creation                 | Creating a MySQL DB instance                                    |
   |                                   |                                                                 |
   |                                   | Creating a MySQL read replica                                   |
   +-----------------------------------+-----------------------------------------------------------------+
   | Instance lifecycle                | Rebooting a MySQL DB instance                                   |
   +-----------------------------------+-----------------------------------------------------------------+
   | Instance modifications            | Scaling up the storage space of a MySQL DB instance             |
   |                                   |                                                                 |
   |                                   | Scale down MySQL instance                                       |
   |                                   |                                                                 |
   |                                   | Changing the MySQL instance type from single to primary/standby |
   |                                   |                                                                 |
   |                                   | Switching MySQL primary/standby DB instances                    |
   |                                   |                                                                 |
   |                                   | Applying for a MySQL private domain name                        |
   |                                   |                                                                 |
   |                                   | Changing a MySQL instance class                                 |
   |                                   |                                                                 |
   |                                   | Configure delayed replication for MySQL                         |
   |                                   |                                                                 |
   |                                   | MySQL flashback                                                 |
   |                                   |                                                                 |
   |                                   | MySQL workload replay                                           |
   +-----------------------------------+-----------------------------------------------------------------+
   | Version upgrade                   | Upgrading a MySQL DB instance engine version                    |
   |                                   |                                                                 |
   |                                   | Upgrade Proxy Instance Version                                  |
   |                                   |                                                                 |
   |                                   | Confirmation after a successful MySQL minor version upgrade     |
   |                                   |                                                                 |
   |                                   | Rollback after a successful MySQL minor version upgrade         |
   +-----------------------------------+-----------------------------------------------------------------+
   | Backup and restoration            | MySQL database-level PITR                                       |
   |                                   |                                                                 |
   |                                   | Restoring to a new MySQL DB instance                            |
   |                                   |                                                                 |
   |                                   | Restoring to an existing MySQL DB instance                      |
   |                                   |                                                                 |
   |                                   | Restoring a MySQL DB Instance to the Current DB Instance        |
   +-----------------------------------+-----------------------------------------------------------------+
   | DBA Assistant                     | Clearing MySQL table fragments                                  |
   +-----------------------------------+-----------------------------------------------------------------+
   | Security and encryption           | MySQL instance disk encryption                                  |
   +-----------------------------------+-----------------------------------------------------------------+

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
