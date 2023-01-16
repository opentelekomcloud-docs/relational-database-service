:original_name: rds_faq_0029.html

.. _rds_faq_0029:

How Can I Install the PostgreSQL Client?
========================================

PostgreSQL provides `client installation packages <https://yum.postgresql.org/>`__ and the required dynamic shared library packages for different OSs on its official website.

.. important::

   Ensure that the database client matches the DB engine version of your RDS PostgreSQL DB instances.

This following uses `PostgreSQL 9.5 <https://yum.postgresql.org/9.5/redhat/rhel-6-x86_64/repoview/postgresqldbserver95.group.html>`__ in Red Hat Linux 6 as an example to describe how to obtain the required installation package and complete the installation.

Procedure
---------

#. Obtain the PostgreSQL client installation package.

   Find the `link <https://yum.postgresql.org/9.5/redhat/rhel-6-x86_64/repoview/postgresql95.html>`__ to the required version on the download page. postgresql95 is used as an example in the following figure.


   .. figure:: /_static/images/en-us_image_0000001419863866.png
      :alt: **Figure 1** Downloading the PostgreSQL client installation package

      **Figure 1** Downloading the PostgreSQL client installation package

#. Obtain the dynamic shared library package required for the PostgreSQL client.

   Find the `link <https://yum.postgresql.org/9.5/redhat/rhel-6-x86_64/repoview/postgresql95-libs.html>`__ to the required version on the download page. postgresql95-libs is used as an example in the following figure.


   .. figure:: /_static/images/en-us_image_0000001420023818.png
      :alt: **Figure 2** Downloading the dynamic shared library package

      **Figure 2** Downloading the dynamic shared library package

#. Upload the installation and dynamic shared library packages to the ECS.

   a. When you create an ECS, select an OS, such as Red Hat 6.6, and bind an EIP to it.
   b. Use a remote connection tool to connect to the ECS through the bound EIP and upload the installation package and dynamic dependency package to the ECS.

#. Run the following command to install the PostgreSQL client:

   .. code-block::

      sudo rpm -ivh postgresql95-9.5.7-1PGDG.rhel6.x86_64.rpm postgresql95-libs-9.5.7-1PGDG.rhel6.x86_64.rpm

   .. note::

      -  If there are any conflicts during the installation, add the **replacefiles** parameter to the command and try to install the client again. Example:

         .. code-block::

            rpm -ivh --replacefiles postgresql95-9.5.7-1PGDG.rhel6.x86_64.rpm postgresql95-libs-9.5.7-1PGDG.rhel6.x86_64.rpm

      -  If a message is displayed prompting you to install a dependency package, you can add the **nodeps** parameter to the command and install the client again. Example:

         .. code-block::

            rpm -ivh --nodeps postgresql95-9.5.7-1PGDG.rhel6.x86_64.rpm postgresql95-libs-9.5.7-1PGDG.rhel6.x86_64.rpm
