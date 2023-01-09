:original_name: rds_pg_configuration.html

.. _rds_pg_configuration:

Modifying Instance Parameters
=============================

You can modify parameters in a custom parameter template to optimize RDS database performance.

You can change parameter values in custom parameter templates only and cannot change parameter values in default parameter templates. When you change parameter values in a custom parameter template, the changes take effect for all DB instances that the parameter template applies to.

When you modify a parameter, the time when the modification takes effect is determined by the type of the parameter.

The RDS console displays the statuses of DB instances that the parameter template applies to. For example, if the DB instance has not yet used the latest modifications made to its parameter template, its status is **Parameter change. Pending reboot**. Manually reboot the DB instance for the latest modifications to take effect for that DB instance.

.. note::

   RDS has default parameter templates whose parameter values cannot be changed. You can view these parameter values by clicking the default parameter templates. If a custom parameter template is set incorrectly, the database startup may fail. If this happens, you can re-configure the custom parameter template based on the settings of the default parameter template.

Modifying Parameters of a DB Instance
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   Available operations are **Save**, **Cancel**, and **Preview**:

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

   .. important::

      In the **Effective upon Reboot** column:

      -  If the value is **Yes** and the DB instance status on the **Instances** page is **Parameter change. Pending reboot**, a reboot is required for the modifications to take effect.

         -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications are also applied to the standby DB instance.)
         -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

      -  If the value is **No**, the modifications take effect immediately.

   After parameters are modified, you can view parameter change history by referring to section :ref:`Viewing Parameter Change History <rds_pg_05_0099>`.

Modifying Parameter Template Parameters
---------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. Choose **Parameter Template Management** in the navigation pane on the left. On the **Custom Templates** page, click the target parameter template.

#. On the **Parameters** page, modify parameters as required.

   Available operations are **Save**, **Cancel**, and **Preview**:

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After the parameter values are modified, you can click **View Change History** to view the modification details.

#. The modifications take effect only after you apply the parameter template to DB instances. For details, see :ref:`Applying a Parameter Template <rds_pg_05_0018>`.

#. View the status of the DB instance to which the parameter template was applied.

   If the DB instance status is **Parameter change. Pending reboot**, a reboot is required for the modifications to take effect.

   -  A DB instance reboot caused by instance class changes will not make parameter modifications take effect.
   -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications are also applied to the standby DB instance.)
   -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
.. |image2| image:: /_static/images/en-us_image_0000001470260233.png
