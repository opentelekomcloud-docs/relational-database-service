:original_name: rds_faq_0027.html

.. _rds_faq_0027:

How Can I Install the MySQL Client?
===================================

MySQL provides client installation packages for different OSs on its official website. MySQL 8.0 is used as an example. You can download the `latest version <https://dev.mysql.com/downloads/mysql/8.0.html#downloads>`__ or `any other version <http://downloads.mysql.com/archives/community/>`__ for your project. The following procedure illustrates how to obtain the required installation package and install the MySQL client into a Red Hat Linux system.

Procedure
---------

#. Obtain the installation package.

   Find the `link <http://downloads.mysql.com/archives/community/>`__ to the required version on the download page. mysql-community-client-8.0.26-1.el8.x86_64.rpm is used as an example in the following figure.


   .. figure:: /_static/images/en-us_image_0000001934653410.png
      :alt: **Figure 1** Download

      **Figure 1** Download

#. Upload the installation package to the ECS.

   a. When you create an ECS, select an OS, such as Red Hat 8.8, and bind an EIP to it.
   b. Use a remote connection tool to connect to the ECS through the bound EIP and upload the installation package to the ECS.

#. Run the following command to install the MySQL client:

   .. code-block:: text

      rpm -ivh --nodeps mysql-community-client-8.0.26-1.el8.x86_64.rpm
