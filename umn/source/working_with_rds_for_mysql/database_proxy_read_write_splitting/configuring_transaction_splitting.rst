:original_name: rds_11_0047.html

.. _rds_11_0047:

Configuring Transaction Splitting
=================================

Scenarios
---------

In most cases, an RDS for MySQL proxy instance sends all requests in transactions to the primary DB instance to ensure transaction correctness. However, in some frameworks, all requests are encapsulated into transactions that are not automatically committed using **set autocommit=0**. This causes heavy loads on the primary DB instance.

Function
--------

Database proxies support transaction splitting. With this feature enabled, RDS can route the read requests prior to write operations in a transaction to read replicas, reducing the pressure of the primary DB instance.

Transaction splitting is disabled by default. If it is enabled under the default READ COMMITTED transaction isolation, RDS only starts a transaction for write operations when automatic commit is disabled. Before the transaction starts, read requests are routed to read replicas through load balancers.

Precautions
-----------

Enabling transaction splitting affects global consistency of certain workloads. Before enabling this feature, evaluate its impact on your workloads.


Configuring Transaction Splitting
---------------------------------

Contact customer service to disable or enable transaction splitting at any time if necessary.

.. note::

   Transaction splitting takes effect only for connections established after this feature is enabled or disabled.

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the primary instance name. The **Basic Information** page is displayed.
#. In the navigation pane on the left, click **Database Proxy**.
#. On the displayed page, click |image2| next to **Transaction Splitting**.
#. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001533364453.png
