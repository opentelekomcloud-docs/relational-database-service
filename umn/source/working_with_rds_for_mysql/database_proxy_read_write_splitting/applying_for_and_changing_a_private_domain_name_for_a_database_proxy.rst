:original_name: rds_11_0066.html

.. _rds_11_0066:

Applying for and Changing a Private Domain Name for a Database Proxy
====================================================================

Scenarios
---------

After a database proxy is created, you can apply for a private domain name for it and change the domain name later as needed.

Precautions
-----------

-  The private domain name must be unique in a given region.
-  Changing the private domain name for a database proxy will interrupt your database connection. To reconnect to the proxy, change the connection address of your applications. The new private domain name is applied to the proxy about 5 minutes after the change.

Applying for a private domain name
----------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Database Proxy**.
#. In the proxy information area, click **Apply** next to the **Private Domain Name** field.
#. In the displayed dialog box, click **OK**.

Changing a Private Domain Name
------------------------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Database Proxy**.
#. In the proxy information area, click **Change** next to the **Private Domain Name** field.
#. In the displayed dialog box, enter a new domain name and click **OK**.

   -  Only the prefix of the private domain name can be modified.
   -  The prefix of a private domain name contains 8 to 63 characters, and can include only lowercase letters and digits.
   -  The new private domain name must be different from any existing ones.

#. If the private domain name is no longer needed, click **Delete** next to the **Private Domain Name** field.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211679.png
