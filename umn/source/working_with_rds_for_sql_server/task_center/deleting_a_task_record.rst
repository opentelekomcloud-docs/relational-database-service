:original_name: rds_sqlserver_task_0002.html

.. _rds_sqlserver_task_0002:

Deleting a Task Record
======================

You can delete task records so that they are no longer displayed in the task list. This operation only deletes the task records, and does not delete the DB instances or terminate the tasks that are being executed.

.. important::

   Deleted task records cannot be recovered. Exercise caution when performing this operation.

Deleting an Instant Task Record
-------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. Choose **Task Center** in the navigation pane on the left. On the displayed **Instant Tasks** page, locate the target task record to be deleted and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.

   You can delete the records of instant tasks in any of the following statuses:

   -  Running
   -  Completed
   -  Failed

Deleting a Scheduled Task Record
--------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. Choose **Task Center** in the navigation pane on the left. On the **Scheduled Tasks** page, locate the target task record to be deleted and check whether the task status is **To be executed** or **To be authorized**.

   -  If yes, go to :ref:`5 <rds_sqlserver_task_0002__rds_task_0002_li1292524805>`.
   -  If no, go to :ref:`6 <rds_sqlserver_task_0002__rds_task_0002_li1922645916559>`.

#. .. _rds_sqlserver_task_0002__rds_task_0002_li1292524805:

   Click **Cancel** in the **Operation** column. In the displayed dialog box, click **Yes** to cancel the task. Then, click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes** to delete the task record.

#. .. _rds_sqlserver_task_0002__rds_task_0002_li1922645916559:

   Click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes** to delete the task record.

   You can delete the records of scheduled tasks in any of the following statuses:

   -  Running
   -  Completed
   -  Failed
   -  Canceled
   -  To be executed
   -  To be authorized

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001470260233.png
