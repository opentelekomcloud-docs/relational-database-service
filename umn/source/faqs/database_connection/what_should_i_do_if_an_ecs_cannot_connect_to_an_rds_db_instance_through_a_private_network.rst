:original_name: rds_faq_0020.html

.. _rds_faq_0020:

What Should I Do If an ECS Cannot Connect to an RDS DB Instance Through a Private Network?
==========================================================================================

Perform the following steps to identify the problem:

#. Check whether the ECS and RDS DB instances are located in the same VPC.

   -  If they are in the same VPC, go to :ref:`2 <rds_faq_0020__l76760374fb794a8d9b961321c13f386d>`.
   -  If they are in different VPCs, create an ECS in the VPC in which the RDS DB instance is located.

#. .. _rds_faq_0020__l76760374fb794a8d9b961321c13f386d:

   Check whether a security group has been added to the ECS.

   -  If a security group has been added, check whether the rules are configured correctly.

      For MySQL DB instances, see the security group description in :ref:`Step 1: Create a DB Instance <rds_02_0008>`. Then, go to :ref:`3 <rds_faq_0020__lbdf6c75fe0be4c37879e3354bc192d36>`.

      For PostgreSQL DB instances, see the security group description in :ref:`Step 1: Create a DB Instance <rds_03_0065>`. Then, go to :ref:`3 <rds_faq_0020__lbdf6c75fe0be4c37879e3354bc192d36>`.

      For Microsoft SQL Server DB instances, see the security group description in :ref:`Step 1: Create a DB Instance <rds_04_0061>`. Then, go to :ref:`3 <rds_faq_0020__lbdf6c75fe0be4c37879e3354bc192d36>`.

   -  If no security group has been added, go to the VPC console from the ECS details page and click **Security Groups** to add a security group.

#. .. _rds_faq_0020__lbdf6c75fe0be4c37879e3354bc192d36:

   On the ECS, check whether the RDS DB instance port can be connected.

   The default port of RDS for MySQL is **3306**.

   The default port of RDS for PostgreSQL is **5432**.

   The default RDS for Microsoft SQL Server port number is **1433**.

   .. code-block::

      telnet <IP address> {port number}

   -  If the ECS can connect to the RDS DB instance port, the network between the ECS and the RDS DB instance is normal and no further action is required.
   -  If the ECS still cannot connect to the port, contact technical support.
