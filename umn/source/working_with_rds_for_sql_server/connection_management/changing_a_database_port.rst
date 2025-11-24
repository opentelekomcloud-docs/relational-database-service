:original_name: rds_sqlserver_change_database_port.html

.. _rds_sqlserver_change_database_port:

Changing a Database Port
========================

**Scenarios**
-------------

This section describes how to change the database port of a primary DB instance or a read replica. For primary/standby DB instances, changing the database port of the primary DB instance will cause the database port of the standby DB instance to also be changed accordingly.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance or click |image2| first and then click the target read replica.
#. On the **Overview** page, find **Database Port** and click **Configure** under it

   .. note::

      For RDS for SQL Server 2022 Enterprise Edition, 2022 Standard Edition, 2019 Enterprise Edition, 2019 Standard Edition, 2017 Enterprise Edition, and 2017 Standard Edition, the port number can be set to 1433 (default) or 2100 to 9500 (excluding 5050, 5353, 5355, 5985, and 5986).

   -  In the displayed dialog box, enter a new port and click **Yes**.

      -  If you change the database port of the primary DB instance, that of the standby DB instance will also be changed.
      -  This process takes 1-5 minutes.

   -  In the dialog box, click **No** to cancel the modification.

#. View the results on the **Overview** page.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000002492831361.png
