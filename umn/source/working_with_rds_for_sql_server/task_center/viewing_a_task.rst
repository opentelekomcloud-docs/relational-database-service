:original_name: rds_sqlserver_task_0001.html

.. _rds_sqlserver_task_0001:

Viewing a Task
==============

You can view the progress and results of tasks on the **Task Center** page.

Supported Tasks
---------------

.. table:: **Table 1** Supported tasks

   +-----------------------------------+------------------------------------------------------------------------+
   | Category                          | Task Name                                                              |
   +===================================+========================================================================+
   | Instance creation                 | Creating a Microsoft SQL Server DB instance                            |
   |                                   |                                                                        |
   |                                   | Creating a Microsoft SQL Server read replica                           |
   +-----------------------------------+------------------------------------------------------------------------+
   | Instance lifecycle                | Rebooting a Microsoft SQL Server DB instance                           |
   |                                   |                                                                        |
   |                                   | Stop Microsoft SQL Server instance                                     |
   |                                   |                                                                        |
   |                                   | Start Microsoft SQL Server instance                                    |
   |                                   |                                                                        |
   |                                   | Delete Microsoft SQL Server instance                                   |
   +-----------------------------------+------------------------------------------------------------------------+
   | Instance modifications            | Scaling a Microsoft SQL Server DB instance                             |
   |                                   |                                                                        |
   |                                   | Switching Microsoft SQL Server primary/standby DB instances            |
   |                                   |                                                                        |
   |                                   | Microsoft SQL Server time zone change                                  |
   |                                   |                                                                        |
   |                                   | Clone Microsoft SQL Server instance                                    |
   |                                   |                                                                        |
   |                                   | Change storage type of Microsoft SQL Server                            |
   |                                   |                                                                        |
   |                                   | Change instance class of Microsoft SQL Server                          |
   +-----------------------------------+------------------------------------------------------------------------+
   | Connection management             | Update SSL certificate for Microsoft SQL Server                        |
   |                                   |                                                                        |
   |                                   | Enabling public accessibility for a Microsoft SQL Server DB instance   |
   |                                   |                                                                        |
   |                                   | Disabling public accessibility for a Microsoft SQL Server DB instance  |
   |                                   |                                                                        |
   |                                   | Create public zone for Microsoft SQL Server                            |
   |                                   |                                                                        |
   |                                   | Change private zone for Microsoft SQL Server                           |
   |                                   |                                                                        |
   |                                   | Change public zone for Microsoft SQL Server                            |
   |                                   |                                                                        |
   |                                   | Create private zone for Microsoft SQL Server                           |
   +-----------------------------------+------------------------------------------------------------------------+
   | Backup and restoration            | Restoring to a new Microsoft SQL Server DB instance                    |
   |                                   |                                                                        |
   |                                   | Restoring data to an existing RDS for Microsoft SQL Server DB instance |
   +-----------------------------------+------------------------------------------------------------------------+
   | Security and encryption           | Enable TDE for Microsoft SQL Server                                    |
   |                                   |                                                                        |
   |                                   | Rotate TDE certificate for Microsoft SQL Server                        |
   +-----------------------------------+------------------------------------------------------------------------+

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
