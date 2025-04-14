:original_name: rds_sql_auditing_log.html

.. _rds_sql_auditing_log:

Enabling the SQL Audit Function
===============================

After you enable the SQL audit function, all SQL operations will be recorded in log files. You can :ref:`download <rds_download_sql_auditing_log>` audit logs to view log details.

By default, SQL audit is disabled because enabling this function may affect database performance. This section describes how to enable, modify, or disable SQL audit.

.. note::

   -  After you enable the SQL audit function, the system records all SQL operations and uploads logs every half an hour or when the size is accumulated to 100 MB.
   -  After SQL audit is enabled, log files will occupy your backup space.

Constraints
-----------

Only the versions listed below support SQL audit. .

-  MySQL 5.7.23 and later versions for DB instances using cloud disks, MySQL 5.7.29.3 and later versions for DB instances using local disks
-  MySQL 8.0

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **SQL Audits**. On the displayed page, click **Set SQL Audit** above the list. In the displayed dialog box, configure information as required and click **OK**.

   **Enabling or setting SQL audit**

   -  To retain SQL audit logs, set |image2| (disabled) to |image3| (enabled).
   -  Audit logs are retained for 7 days by default but can be retained from anywhere from 1 to 732 days if needed.

   **Disabling SQL audit**

   To disable SQL audit, toggle |image4| (enabled) to |image5| (disabled).

   -  If you select the check box "I acknowledge that after audit log is disabled, all audit logs are deleted.", all audit logs will be deleted.

      .. important::

         Deleted audit logs cannot be recovered. Exercise caution when performing this operation.

   -  If you do not select the check box "I acknowledge that after audit log is disabled, all audit logs are deleted.", the audit logs will be retained.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191131431.png
.. |image3| image:: /_static/images/en-us_image_0000001191211583.png
.. |image4| image:: /_static/images/en-us_image_0000001191211593.png
.. |image5| image:: /_static/images/en-us_image_0000001191211585.png
