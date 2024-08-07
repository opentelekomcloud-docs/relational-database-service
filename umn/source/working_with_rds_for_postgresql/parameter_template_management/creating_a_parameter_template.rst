:original_name: rds_pg_parameter_group.html

.. _rds_pg_parameter_group:

Creating a Parameter Template
=============================

You can use database parameter templates to manage the DB engine configuration. A database parameter template acts as a container for engine configuration values that can be applied to one or more DB instances.

When you create a DB instance, RDS will automatically allocate a default database parameter template for you. This default template contains DB engine defaults and system defaults that are configured based on the engine, compute class, and allocated storage of the instance. Default parameter templates cannot be modified, but you can create your own parameter template to change parameter settings.

.. important::

   Not all of the DB engine parameters in a custom parameter template can be changed.

If you want to use a custom parameter template, you simply create a parameter template and select it when you create a DB instance or apply it to an existing DB instance following the instructions provided in section :ref:`Applying a Parameter Template <rds_05_0018>`.

When you have already created a parameter template and want to include most of the custom parameters and values from that template in a new parameter template, you can replicate that parameter template following the instructions provided in section :ref:`Replicating a Parameter Template <rds_08_0014>`.

The following are the key points you should know when using parameters in a parameter template:

-  The changes to parameter values in a custom parameter template take effect only after you apply the template to DB instances. For details, see :ref:`Applying a Parameter Template <rds_05_0018>`.
-  Improper parameter settings may have unintended consequences, including reduced performance and system instability. Exercise caution when modifying database parameters and you need to back up data before modifying parameters in a parameter template. Before applying parameter template changes to a production DB instance, you should try out these changes on a test DB instance.

.. note::

   RDS does not share parameter template quotas with DDS.

   You can create a maximum of 100 parameter templates for RDS DB instances. All RDS DB engines share the parameter template quota.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Parameter Template Management** page, click **Create Parameter Template**.
#. In the displayed dialog box, configure required information and click **OK**.

   -  Select a DB engine for the parameter template.
   -  The template name must consist of 1 to 64 characters. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.).
   -  The description consists of a maximum of 256 characters and cannot contain carriage return characters or the following special characters: >!<"&'=

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
