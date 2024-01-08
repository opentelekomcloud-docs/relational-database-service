:original_name: rds_05_0018.html

.. _rds_05_0018:

Applying a Parameter Template
=============================

**Scenarios**
-------------

You can apply parameter templates to DB instances as needed.

-  The parameter **innodb_buffer_pool_size** is determined by the memory. DB instances of different specifications have different value ranges. If this parameter value is out of range of the DB instance that the parameter template applies to, the maximum value within the range is used.
-  A parameter template can be applied only to DB instances of the same DB engine version.

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

   After the parameter template is successfully applied, you can view the application records by referring to section :ref:`Viewing Application Records of a Parameter Template <rds_05_0098>`.

.. |image1| image:: /_static/images/en-us_image_0000001744574182.png
