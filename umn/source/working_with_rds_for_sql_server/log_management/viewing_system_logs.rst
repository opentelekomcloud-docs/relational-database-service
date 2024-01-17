:original_name: rds_sqlserver_01_0002.html

.. _rds_sqlserver_01_0002:

Viewing System Logs
===================

**Scenarios**
-------------

System logs contain logs generated during the database running. These can help you analyze problems with the database.

Viewing Log Details
-------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Logs**. On the **System Logs** page, view details about system logs.

   -  You can select a log level in the upper right corner to view logs of the selected level.

      .. note::

         For Microsoft SQL Server DB instances, only info-level logs are displayed currently.

   -  You can click |image2| in the upper right corner to view logs generated in different time segments.
   -  If the description of a log is truncated, locate the log and move your pointer over the description in the **Description** column to view details.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001145211382.png
