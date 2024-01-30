:original_name: rds_mysql_error_log.html

.. _rds_mysql_error_log:

Viewing Error Logs
==================

RDS log management allows you to view database-level logs, including error logs and slow SQL query logs.

Error logs contain warning- and error-level logs generated during the database running. These can help you analyze problems with the database.

Viewing Log Details
-------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Logs**. On the **Error Logs** page, view details about error logs.

   -  You can select a log level in the upper right corner to view logs of the selected level.

      .. note::

         For MySQL DB instances, the following levels of logs are displayed:

         -  ERROR
         -  WARNING
         -  NOTE

   -  You can click |image2| in the upper right corner to view error logs generated in different time segments.
   -  If the description of a log is truncated, locate the log and move your pointer over the description in the **Description** column to view details.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
.. |image2| image:: /_static/images/en-us_image_0000001739973828.png
