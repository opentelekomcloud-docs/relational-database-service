:original_name: rds_faq_0029.html

.. _rds_faq_0029:

How Can I Install the PostgreSQL Client?
========================================

The PostgreSQL community provides `client installation methods <https://www.postgresql.org/download/linux/>`__ for different OSs. You can download and install the client using the installation tool of the OS. This installation method is simple but has requirements on the ECS OS. It can be used only for the OSs supported by the PostgreSQL community.

The following describes how to install a PostgreSQL 15 client on Ubuntu.

Procedure
---------

#. Log in to the target ECS.

   a. When you create an ECS, select an OS, such as Ubuntu, and bind an EIP to it.
   b. Use a remote connection tool to connect to the ECS through the EIP.

#. Open the `client installation <https://www.postgresql.org/download/linux/ubuntu/>`__ page.

#. Run the following commands on the ECS to install a PostgreSQL client. If the version included in the Ubuntu version is not the one you want, you can use the PostgreSQL Apt repository.

   .. code-block::

      # Import the repository signing key:
      sudo apt install curl ca-certificates
      sudo install -d /usr/share/postgresql-common/pgdg
      sudo curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc

      # Create the repository configuration file:
      sudo sh -c 'echo "deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

      # Update the package lists:
      sudo apt update

      # Install the latest version of PostgreSQL:
      # If you want a specific version, use 'postgresql-15' or similar instead of 'postgresql'
      sudo apt -y install postgresql-15

#. Run the following command to check whether the client is successfully installed. If the installation is successful, the following information is displayed:

   .. code-block::

      psql -V

   |image1|

.. |image1| image:: /_static/images/en-us_image_0000002218505054.png
