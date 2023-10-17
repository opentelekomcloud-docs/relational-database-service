:original_name: rds_sqlserver_05_0018.html

.. _rds_sqlserver_05_0018:

Applying a Parameter Template
=============================

**Scenarios**
-------------

You can apply parameter templates to DB instances as needed. A parameter template can be applied only to DB instances of the same version.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Parameter Template Management** page, perform the following operations based on the type of the parameter template to be applied:

   -  If you intend to apply a default parameter template to DB instances, click **Default Templates**, locate the target parameter template, and click **Apply** in the **Operation** column.
   -  If you intend to apply a custom parameter template to DB instances, click **Custom Templates**, locate the target parameter template, and choose **More** > **Apply** in the **Operation** column.

   A parameter template can be applied to one or more DB instances.

#. In the displayed dialog box, select one or more DB instances to which the parameter template will be applied and click **OK**.

   After the parameter template is successfully applied, you can view the application records by referring to section :ref:`Viewing Application Records of a Parameter Template <rds_sqlserver_05_0098>`.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
