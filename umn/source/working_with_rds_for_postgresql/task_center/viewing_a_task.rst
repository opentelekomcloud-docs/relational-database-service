:original_name: rds_task_pg_0001.html

.. _rds_task_pg_0001:

Viewing a Task
==============

You can view the detailed progress and result of the task on the **Task Center** page.

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

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Task Center** page, locate the target task and view its details.

   -  To identify the target task, you can use the task name and DB instance name/ID or enter the target task name in the search box in the upper right corner.

   -  You can view the progress and status of tasks in a specific period.

      The retention duration of failed tasks is 7 days, and of completed tasks is 1 days by default. It is controlled by two parameters on background. The retention duration cannot exceed 30 days. To set the retention duration contact O&M personnel.

   -  You can view instant tasks in the following statuses:

      -  Running
      -  Completed
      -  Failed

   -  View the task creation and completion time.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
