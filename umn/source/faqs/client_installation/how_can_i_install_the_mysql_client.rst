:original_name: rds_faq_0027.html

.. _rds_faq_0027:

How Can I Install the MySQL Client?
===================================

MySQL provides client installation packages for different OSs on its official website. MySQL 5.6 is used as an example. Download the `MySQL 5.6 client installation package <http://dev.mysql.com/downloads/mysql/5.6.html#downloads>`__ or `other versions of the packages <http://downloads.mysql.com/archives/community/>`__. The following procedure illustrates how to obtain the required installation package and install the MySQL client into a Red Hat Linux system.

Procedure
---------

#. Obtain the installation package.

   Find the `link <http://dev.mysql.com/downloads/file/?id=463159>`__ to the required version on the download page. MySQL-client-5.6.31-1.el6.x86_64.rpm is used as an example in the following figure.


   .. figure:: /_static/images/en-us_image_0000001420023530.png
      :alt: **Figure 1** Procedure

      **Figure 1** Procedure

   .. note::

      Click `URL <http://dev.mysql.com/get/Downloads/MySQL-5.6/MySQL-client-5.6.31-1.el6.x86_64.rpm>`__ to download the installation package.

#. Upload the installation package to the ECS.

   a. When you create an ECS, select an OS, such as Red Hat 6.6, and bind an EIP to it.
   b. Use a remote connection tool to connect to the ECS through the bound EIP and upload the installation package to the ECS.

#. Run the following command to install the MySQL client:

   .. code-block::

      Sudo rpm -ivh MySQL-client-5.6.31-1.el6.x86_64.rpm

   .. note::

      -  If there are any conflicts during the installation, add the **replacefiles** parameter to the command and try to install the client again. Example:

         .. code-block::

            rpm -ivh --replacefiles MySQL-client-5.6.31-1.el6.x86_64.rpm

      -  If a message is displayed prompting you to install a dependency package, you can add the **nodeps** parameter to the command and install the client again. Example:

         .. code-block::

            rpm -ivh --nodeps MySQL-client-5.6.31-1.el6.x86_64.rpm
