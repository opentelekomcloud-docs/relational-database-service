:original_name: rds_faq_0029.html

.. _rds_faq_0029:

How Can I Install the PostgreSQL Client?
========================================

PostgreSQL provides `client installation methods <https://www.postgresql.org/download/>`__ for different OSs on its official website.

The following describes how to install a PostgreSQL 12 client in CentOS.

Procedure
---------

#. Log in to an ECS.

   a. When you create an ECS, select an OS, such as CentOS 7, and bind an EIP to it.
   b. Use a remote connection tool to connect to the ECS through the EIP.

#. Open the `client installation page <https://www.postgresql.org/download/linux/redhat/>`__.

#. Select a DB engine version, OS, and OS architecture, and run the following commands on the ECS to install a PostgreSQL client.

   .. code-block::

      sudo yum install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
      sudo yum install -y postgresql12-server


   .. figure:: /_static/images/en-us_image_0000001445233198.png
      :alt: **Figure 1** Installing a client

      **Figure 1** Installing a client

   -  Select a DB engine version that is consistent with that of your RDS for PostgreSQL instance.
   -  Select an OS that is consistent with that of the ECS.
   -  Select an OS architecture that is consistent with that of the ECS.


   .. figure:: /_static/images/en-us_image_0000001495233177.png
      :alt: **Figure 2** Installing the RPM package

      **Figure 2** Installing the RPM package


   .. figure:: /_static/images/en-us_image_0000001444753346.png
      :alt: **Figure 3** Client installed

      **Figure 3** Client installed

#. Connect to the RDS for PostgreSQL instance.


   .. figure:: /_static/images/en-us_image_0000001444913286.png
      :alt: **Figure 4** Connection successful

      **Figure 4** Connection successful
