:original_name: rds_change_database_port.html

.. _rds_change_database_port:

Changing a Database Port
========================

**Scenarios**
-------------

This section describes how to change the database port of a primary DB instance or a read replica. For primary/standby DB instances, changing the database port of the primary DB instance will cause the database port of the standby DB instance to also be changed accordingly.

Constraints
-----------

When the database port of a DB instance is being changed, you cannot:

-  Bind an EIP to the DB instance.
-  Delete the DB instance.
-  Create a backup for the DB instance.
-  Restore from backup data or from a specific point in time to the original DB instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance or click |image2| first and then click the target read replica.
#. In the **Connection Information** area on the **Basic Information** page, click |image3| in the **Database Port** field.

   .. note::

      A MySQL database can use ports 2100 to 9500.

   -  To submit the change, click |image4|.

      -  In the dialog box, click **Yes**.

         a. If you change the database port of the primary DB instance, that of the standby DB instance will also be changed and both DB instances will be rebooted.
         b. If you change the database port of a read replica, the change will not affect other DB instances. Only the read replica will be rebooted.
         c. This process takes 1-5 minutes.

      -  In the dialog box, click **No** to cancel the modification.

   -  To cancel the change, click |image5|.

#. View the results on the **Basic Information** page.

.. |image1| image:: /_static/images/en-us_image_0000001786854381.png
.. |image2| image:: /_static/images/en-us_image_0000001786853997.png
.. |image3| image:: /_static/images/en-us_image_0000001739973860.png
.. |image4| image:: /_static/images/en-us_image_0000001786933909.png
.. |image5| image:: /_static/images/en-us_image_0000001786933905.png
