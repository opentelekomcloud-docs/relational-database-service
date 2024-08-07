:original_name: rds_configuration.html

.. _rds_configuration:

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

   For parameter description details, see :ref:`Suggestions on MySQL Parameter Tuning <rds_08_00001>`.

   Available operations are as follows:

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After the parameter values are modified, you can click **View Change History** to view the details.

#. The modifications do not take effect until you apply the parameter template to your DB instances. For details, see :ref:`Applying a Parameter Template <rds_05_0018>`.

#. View the status of the DB instance to which the parameter template was applied.

   If the DB instance status is **Parameter change. Pending reboot**, a reboot is required for the modifications to take effect.

   -  The DB instance reboot caused by instance class changes will not make parameter modifications take effect.
   -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications are also applied to the standby DB instance.)
   -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

Modifying Instance Parameters
-----------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   .. important::

      Check the value in the **Effective upon Reboot** column.

      -  If the value is **Yes** and the DB instance status on the **Instances** page is **Parameter change. Pending reboot**, a reboot is required for the modifications to take effect.

         -  If you have modified parameters of a primary DB instance, you need to reboot the primary DB instance for the modifications to take effect. (For primary/standby DB instances, the parameter modifications are also applied to the standby DB instance.)
         -  If you have modified parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

      -  If the value is **No**, the modifications take effect immediately.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

   After parameters are modified, you can click **Change History** to view parameter modification details.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001191211679.png
