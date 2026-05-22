:original_name: rds_05_0099.html

.. _rds_05_0099:

Viewing Parameter Change History
================================

Scenarios
---------

You can view the change history of DB instance parameters or custom parameter templates.

.. note::

   An exported or custom parameter template has initially a blank change history.

Viewing Parameter Change History of a DB Instance
-------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, click **Change History**.

   You can view the parameter change history within a specified period (no more than two years). By default, the parameter change history of the last seven days is queried.

   You can view the parameter name, original parameter value, new parameter value, modification status, modification time, application status, and application time.

Viewing Change History of a Parameter Template
----------------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. Choose **Parameter Templates** in the navigation pane on the left. On the **Custom Templates** page, click the target parameter template.

#. On the displayed page, choose **Change History** in the navigation pane on the left.

   You can view the parameter name, original parameter value, new parameter value, modification status, and modification time.

   You can apply the parameter template to DB instances as required by referring to :ref:`Applying a Parameter Template <rds_05_0018>`.

Viewing Parameter Changes
-------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. Choose **Parameter Templates** in the navigation pane on the left. On the **Parameter Templates** page, click the **Parameter Changes** tab.

#. Click **View Details** in the **Operation** column.

   You can view detailed information about the modified parameters.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211679.png
.. |image3| image:: /_static/images/en-us_image_0000001191211679.png
