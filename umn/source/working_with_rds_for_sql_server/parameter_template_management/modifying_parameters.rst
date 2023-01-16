:original_name: rds_sqlserver_configuration.html

.. _rds_sqlserver_configuration:

Modifying Parameters
====================

You can modify parameters in a custom parameter template to optimize RDS database performance.

You can only change parameter values in custom parameter templates. You cannot change the parameter values in default parameter templates. When you change parameter values in a custom parameter template, the changes take effect for all DB instances that the parameter template applies to.

When you modify a parameter, the time when the modification takes effect depends on the type of the parameter.

The RDS console displays the statuses of DB instances that the parameter template applies to. For example, if the DB instance has not yet used the latest modifications made to its parameter template, its status is **Parameter change. Pending reboot**. Manually reboot the DB instance for the latest modifications to take effect for that DB instance.

.. note::

   RDS has default parameter templates whose parameter values cannot be changed. You can view these parameter values by clicking the default parameter templates. If a custom parameter template is set incorrectly, the database startup may fail. If this happens, you can re-configure the custom parameter template based on the settings of the default parameter template.

Modifying Parameter Template Parameters
---------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. Choose **Parameter Template Management** in the navigation pane on the left. On the **Custom Templates** page, click the target parameter template.

#. On the **Parameters** page, modify parameters as required.

   Relevant parameters are as follows:

   -  Set **remote access** to **0** (default value) to prevent locally stored procedures from running on a remote server and remotely stored procedures from running on a local server.
   -  The **max server memory (MB)** parameter indicates the server memory. The default value equals to the OS memory (MB) minus 520 (MB). Its minimum value is 1024 MB.

   Available operations are as follows:

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After the parameter values are modified, you can click **View Change History** to view the modification details.

#. The modifications take effect only after you apply the parameter template to DB instances. For details, see :ref:`Applying a Parameter Template <rds_sqlserver_05_0018>`.

#. View the status of the DB instance to which the parameter template was applied.

   If the DB instance status is **Parameter change. Pending reboot**, a reboot is required for the modifications to take effect.

   -  A DB instance reboot caused by instance class changes will not make parameter modifications take effect.
   -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications are also applied to the standby DB instance.)
   -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

Modifying Instance Parameters
-----------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   Relevant parameters are as follows:

   -  Set **remote access** to **0** (default value) to prevent locally stored procedures from running on a remote server and remotely stored procedures from running on a local server.
   -  The **max server memory (MB)** parameter indicates the server memory. The default value equals to the OS memory (MB) minus 520 (MB). Its minimum value is 1024 MB.

   Available operations are **Save**, **Cancel**, and **Preview**.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

   .. important::

      In the **Effective upon Reboot** column:

      -  If the value is **Yes** and the DB instance status on the **Instances** page is **Parameter change. Pending reboot**, a reboot is required the modifications to take effect.

         -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications are also applied to the standby DB instance.)
         -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

      -  If the value is **No**, the modifications take effect immediately.

   After parameters are modified, you can view parameter change history by referring to section :ref:`Viewing Parameter Change History <rds_sqlserver_05_0099>`.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001470260233.png
