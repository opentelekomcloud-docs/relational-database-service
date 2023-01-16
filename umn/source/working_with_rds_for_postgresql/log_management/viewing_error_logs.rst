:original_name: rds_recent_log.html

.. _rds_recent_log:

Viewing Error Logs
==================

**Scenarios**
-------------

Error logs contain logs generated during the database running. These can help you analyze problems with the database.

Viewing Log Details
-------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Logs**. On the **Error Logs** page, view details about error logs.

   -  You can select a log level in the upper right corner of the log list.

      .. note::

         For PostgreSQL DB instances, the following levels of logs are displayed:

         -  ERROR
         -  FATAL
         -  PANIC

   -  You can click |image2| in the upper right corner to view error logs generated in different time segments.
   -  If the description of a log is truncated, locate the log and move your pointer over the description in the **Description** column to view details.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001469940645.png
