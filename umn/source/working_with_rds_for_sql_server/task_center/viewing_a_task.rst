:original_name: rds_sqlserver_task_0001.html

.. _rds_sqlserver_task_0001:

Viewing a Task
==============

You can view the progress and results of tasks on the **Task Center** page.

.. note::

   You can view and manage the following tasks:

   -  Creating DB instances
   -  Creating read replicas
   -  Changing single DB instances to primary/standby
   -  Scaling up storage space
   -  Binding EIPs to DB instances
   -  Unbinding EIPs from DB instances
   -  Switching primary/standby DB instances
   -  Rebooting DB instances
   -  Restoring data to new DB instances

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
