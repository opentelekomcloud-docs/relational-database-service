:original_name: rds_pg_modify_availability.html

.. _rds_pg_modify_availability:

Changing the Failover Priority
==============================

**Scenarios**
-------------

You can configure the failover priority for reliability or for availability, depending on your service requirements.

-  **Reliability**: This option is selected by default. Data consistency is preferentially ensured during a primary/standby failover. This is recommended for users whose highest priority is data consistency.
-  **Availability**: Database availability is preferentially ensured during a primary/standby failover. This is recommended for users who require their databases to provide uninterrupted online services.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the primary instance name.
#. On the displayed **Overview** page, find **Failover Priority** and click **Configure** under it. In the displayed dialog box, select a priority and click **OK**.
#. View the results on the **Overview** page.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
