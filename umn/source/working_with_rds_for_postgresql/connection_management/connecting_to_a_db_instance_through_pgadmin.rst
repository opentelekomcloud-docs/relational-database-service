:original_name: rds_pg_11_0005.html

.. _rds_pg_11_0005:

Connecting to a DB Instance Through pgAdmin
===========================================

You can use the pgAdmin client to connect to an RDS DB instance.

.. important::

   The pgAdmin version must be 4 or later.

**Preparations**
----------------

#. Prepare an **ECS** or a device that can access RDS DB instances.

   To connect to a DB instance through a floating IP address, you must:

   -  Ensure that the ECS and DB instance must be in the same VPC.
   -  Ensure that the ECS must be allowed by the security group to access RDS DB instances.

   To connect to a DB instance through an EIP, you must:

   a. Bind the EIP to the DB instance. For details, see :ref:`Binding an EIP <rds_03_0064>`.
   b. Ensure that the local device can access the EIP that has been bound to the DB instance.

#. Install the pgAdmin client on the prepared ECS or device.

Procedure
---------

#. Start pgAdmin.

#. .. _rds_pg_11_0005__li1454192935019:

   In the displayed login window, choose **Servers** > **Create** > **Server**.


   .. figure:: /_static/images/en-us_image_0000001191211507.png
      :alt: **Figure 1** Creation

      **Figure 1** Creation

#. On the **General** page, specify **Name**. On the **Connection** page, specify information about the DB instance to be connected. Then, click **Save**.


   .. figure:: /_static/images/en-us_image_0000001145211472.png
      :alt: **Figure 2** General page

      **Figure 2** General page


   .. figure:: /_static/images/en-us_image_0000001145211470.png
      :alt: **Figure 3** Connection page

      **Figure 3** Connection page

   Parameter description:

   -  **Host name/address**: indicates the IP address of the DB instance you want to connect to. If you connect to a DB instance through a floating IP address, enter the floating IP address displayed in the **Connection Information** area on the **Basic Information** page of your DB instance. If you connect to a DB instance through an EIP, enter the EIP of your DB instance.
   -  **Port**: indicates the database port. By default, the value is **5432**.
   -  **User name**: indicates the username. By default, the value is **root**.
   -  **Password**: indicates the password of the target database username.

#. In the login window, check that the connection information is correct. The target DB instance is successfully connected.
