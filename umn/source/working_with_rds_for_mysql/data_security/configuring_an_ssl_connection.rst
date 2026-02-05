:original_name: rds_mysql_0001.html

.. _rds_mysql_0001:

Configuring an SSL Connection
=============================

Secure Socket Layer (SSL) is an encryption-based Internet security protocol for establishing an encrypted link between a server and a client. It provides authenticated Internet connections to ensure the privacy and integrity of online communications. SSL:

-  Authenticates users and servers, ensuring that data is sent to the correct clients and servers.
-  Encrypts data, preventing it from being intercepted during transmission.
-  Ensures data integrity during transmission.

Clients using versions earlier than 5.1 have SSL compatibility issues. By default, SSL is disabled for new RDS for MySQL instances. If your client has no SSL compatibility issues, you can enable SSL by referring to :ref:`Enabling SSL <rds_mysql_0001__section52887001420>`. Enabling SSL will increase the network connection response time and CPU resource consumption. Before enabling it, evaluate any potential impacts on service performance. If a client cannot connect to the DB instance due to compatibility issues, upgrade the client and try again.

You can connect to a DB instance through a client using an SSL or non-SSL connection.

-  If SSL is disabled (default), use a non-SSL connection.
-  If SSL is enabled, use an SSL connection. SSL encrypts connections to the instance, making in-transit data more secure.

Constraints
-----------

Enabling or disabling SSL will cause instances to reboot and interrupt connections. Exercise caution when performing this operation.

.. _rds_mysql_0001__section52887001420:

Enabling SSL
------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. On the **Overview** page, find **SSL** and click **Enable**.

   Alternatively, in the navigation pane on the left, choose **Connectivity & Security**. In the **Connection Information** area, click |image2| in the **SSL** field.

#. In the displayed dialog box, click **OK**.

#. After a while, check the SSL status on the **Overview** page. It is enabled.

Disabling SSL
-------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. On the **Overview** page, find **SSL** and click **Disable**.

   Alternatively, in the navigation pane on the left, choose **Connectivity & Security**. In the **Connection Information** area, click |image4| in the **SSL** field.

#. In the displayed dialog box, click **OK**.

#. After a while, check the SSL status on the **Overview** page. It is disabled.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000002492045012.png
.. |image3| image:: /_static/images/en-us_image_0000001191211679.png
.. |image4| image:: /_static/images/en-us_image_0000002492048460.png
