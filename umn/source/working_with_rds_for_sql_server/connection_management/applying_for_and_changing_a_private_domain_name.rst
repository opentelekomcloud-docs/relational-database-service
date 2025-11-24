:original_name: rds_sqlserver_0024.html

.. _rds_sqlserver_0024:

Applying for and Changing a Private Domain Name
===============================================

You can apply for a private domain name and connect to your RDS DB instance through the private domain name.

Constraints
-----------

After a private domain name is generated, changing the floating IP address will interrupt database connections. Exercise caution when performing this operation.

Applying for a Private Domain Name
----------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the DB instance name to go to the **Overview** page.

#. Under **Private Domain Name**, click **Apply**.

   Alternatively, in the navigation pane on the left, choose **Connectivity & Security**. On the displayed page, click **Apply** next to the **Private Domain Name** field.

#. In the **Private Domain Name** field, view the generated private domain name.

Changing a Private Domain Name
------------------------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the DB instance name to go to the **Overview** page.
#. Under **Private Domain Name**, click **Configure**.
#. In the displayed dialog box, enter a new private domain name. Click **OK**.

   .. note::

      -  Only the prefix of a private domain name can be modified.
      -  The prefix of a private domain name can contain 8 to 63 characters, and can include only letters and digits.
      -  The new private domain name must be different from the existing ones.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211679.png
