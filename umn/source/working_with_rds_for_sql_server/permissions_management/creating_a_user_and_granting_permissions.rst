:original_name: rds_sqlserver_07_0002.html

.. _rds_sqlserver_07_0002:

Creating a User and Granting Permissions
========================================

This chapter describes how to use `Identity and Access Management (IAM) <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__ for fine-grained permissions management for your RDS resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing RDS resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or cloud service to perform efficient O&M on your RDS resources.

If your account does not require individual IAM users, skip this chapter.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <rds_sqlserver_07_0002__rds_07_0002_en-us_topic_0172661625_fig15451536531>`).

Prerequisites
-------------

Learn about the permissions (see :ref:`Permissions Management <rds_01_0017>`) supported by RDS and choose policies or roles according to your requirements.For the system policies of other services, see `Permissions <https://docs.otc.t-systems.com/permissions/index.html>`__.

Process Flow
------------

.. _rds_sqlserver_07_0002__rds_07_0002_en-us_topic_0172661625_fig15451536531:

.. figure:: /_static/images/en-us_image_0192954081.png
   :alt: **Figure 1** Process for granting RDS permissions

   **Figure 1** Process for granting RDS permissions

#. .. _rds_sqlserver_07_0002__rds_07_0002_en-us_topic_0172661625_li10176121316284:

   `Create a user group and assign permissions <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__ to it.

   Create a user group on the IAM console, and attach the **RDS ReadOnlyAccess** policy to the group.

   .. note::

      To use some interconnected services, you also need to configure permissions of such services.

      For example, to connect to your DB instance through the console, configure the **DAS FullAccess** permission of Data Admin Service (DAS) besides **RDS ReadOnlyAccess**.

#. `Create an IAM user and add it to the user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <rds_sqlserver_07_0002__rds_07_0002_en-us_topic_0172661625_li10176121316284>`.

#. `Log in <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.

   Log in to the RDS console by using the created user, and verify that the user only has read permissions for RDS.

   -  Choose **Service List** > **Relational Database Service** and click **Buy DB Instance**. If a message appears indicating that you have insufficient permissions to perform the operation, the **RDS ReadOnlyAccess** policy has already been applied.
   -  Choose any other service in **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the **RDS ReadOnlyAccess** policy has already taken effect.
