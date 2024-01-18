:original_name: rds_pg_08_0042.html

.. _rds_pg_08_0042:

Exporting a Parameter Template
==============================

**Scenarios**
-------------

-  You can export a parameter template of a DB instance for future use. You can also apply the exported parameter template to DB instances by referring to :ref:`Applying a Parameter Template <rds_pg_05_0018>`.
-  You can export the parameter template information (parameter names, values, and descriptions) of a DB instance to a CSV file for viewing and analysis.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Parameters**. On the displayed page, click **Export** above the parameter list.

   -  Exporting to a custom template

      In the displayed dialog box, configure required information and click **OK**.

      .. note::

         -  The template name must consist of 1 to 64 characters. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.).
         -  The description consists of a maximum of 256 characters and cannot contain carriage return characters or the following special characters: >!<"&'=

      After the parameter template is exported, a new template is generated in the list on the **Parameter Template Management** page.

   -  Exporting to a file

      The parameter template information (parameter names, values, and descriptions) of a DB instance is exported to a CSV file. In the displayed dialog box, enter the file name and click **OK**.

      .. note::

         The file name must start with a letter and consist of 4 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.

.. |image1| image:: /_static/images/en-us_image_0000001744574182.png
