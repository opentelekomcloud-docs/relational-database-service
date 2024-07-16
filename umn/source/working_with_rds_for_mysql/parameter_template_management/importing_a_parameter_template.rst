:original_name: rds_08_0043.html

.. _rds_08_0043:

Importing a Parameter Template
==============================

Scenarios
---------

RDS allows you to import new parameter templates for future use. To apply an imported parameter template to new DB instances, see :ref:`Applying a Parameter Template <rds_05_0018>`.

Constraints
-----------

-  Only parameter templates that were exported from the **Parameter Templates** page on the RDS console can be imported.
-  If any modification to an exported parameter template causes a change in the file format, the template may not be able to be imported.
-  The parameter template to be imported cannot contain parameters related to specifications. For details about such parameters, see :ref:`Constraints <en-us_topic_scale_rds__section17604457192012>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Parameter Templates** page, click **Import Parameter Template**.

#. In the displayed dialog box, select a DB engine version, enter a new parameter template name, click **Select File**, select the target parameter list (containing parameter names, values, and description), and click **OK**.

   Only one file (CSV format) can be imported at a time. The file size cannot exceed 50 KB.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
