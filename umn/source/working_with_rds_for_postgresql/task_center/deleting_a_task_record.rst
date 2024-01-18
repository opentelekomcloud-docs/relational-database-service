:original_name: rds_task_pg_0002.html

.. _rds_task_pg_0002:

Deleting a Task Record
======================

You can delete task records so that they are no longer displayed in the task list. This operation only deletes the task records, and does not delete the DB instances or terminate the tasks that are being executed.

.. important::

   Deleted task records cannot be recovered. Exercise caution when performing this operation.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. Choose **Task Center** in the navigation pane on the left. On the displayed page, locate the target task record to be deleted and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.

   You can delete the records of instant tasks in any of the following statuses:

   -  Running
   -  Completed
   -  Failed

.. |image1| image:: /_static/images/en-us_image_0000001744574182.png
