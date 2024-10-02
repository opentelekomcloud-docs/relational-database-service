:original_name: rds_pg_05_0004.html

.. _rds_pg_05_0004:

Upgrading the Major Version of a DB Instance on the Console
===========================================================

Scenarios
---------

RDS for PostgreSQL allows you to upgrade the major version of your DB instance in either of the following methods:

-  Upgrade without cutover: You can use it to test service compatibility of a new version. Upgrading a major version may cause service compatibility issues. A compatibility test is strongly recommended. After the test is passed, perform an upgrade in cutover mode. An upgrade without service cutover will not affect the original instance.
-  Upgrade with cutover: During an upgrade, the original instance is set to read-only and services are interrupted for minutes. After the upgrade is complete, the original and new instances automatically exchange their virtual IP addresses and the application connection will be switched to the new instance. No changes need to be made to your application.

Constraints
-----------

-  Major version upgrades are available to the following versions:

   -  RDS for PostgreSQL 12: 12.7 or later
   -  RDS for PostgreSQL 13: 13.3 or later
   -  RDS for PostgreSQL 14: 14.4 or later
   -  Major version upgrades are unavailable to RDS for PostgreSQL 11.

-  Due to OS restrictions, some instances do not support major version upgrades. To learn which versions your instance can be upgraded to, see the list of available versions on the **Major Version Upgrade** page.
-  Before a major version upgrade, perform an upgrade check. If there is no successful upgrade check in the validity period, a major version upgrade is not allowed.

Precautions
-----------

-  After a major version upgrade is complete, rollback cannot be performed. Before upgrading a major version, perform a thorough test.
-  After a major version upgrade is complete, a new DB instance is created. The original DB instance is still retained and billed. You can release the original instance when the workloads on the new instance run stably.
-  Read replicas do not support major version upgrades. If your DB instance has read replicas and DR instances, the read replicas and DR instances will not be upgraded synchronously. You need to create them again after a major version upgrade. For details, see :ref:`Creating a Read Replica <rds_add_read_replica_pg>`.
-  A major version upgrade has the following impacts:

   -  If you upgrade your instance with service cutover, the instance will be set to read-only during the upgrade and services will be interrupted for minutes. Perform the upgrade during off-peak hours. If you upgrade your instance without service cutover, there is no impact on your services.

      .. important::

         The **default_transaction_read_only** parameter controls the read-only settings. Before the upgrade, check whether any modification has been made to this parameter. If yes, the data inserted into the instance during the cutover will be lost after the upgrade.

   -  After a major version upgrade:

      -  Parameter modifications in the original instance are automatically synchronized to the new instance.
      -  If the original instance uses any parameter that is not supported by the new version, the parameter will be automatically deleted from the new instance.
      -  If the value of any parameter in the original instance is not within the valid range configured in the new version, the new instance will use the default value defined in the parameter template of the new version.

-  Upgrading a major version will not upgrade the versions of plugins. For details about supported plugin versions, see :ref:`Supported Plugins <rds_09_0045>`. If the new instance supports any plugin of a later version, you can run **ALTER EXTENSION extension_name UPDATE TO 'new_version';** to update the plugin, or uninstall and reinstall the plugin of the latest version.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **Major Version Upgrade**.
#. On the displayed page, select the target version, click **Check Now**, and wait for several minutes.

   .. note::

      -  If plugins are installed on the instance after a successful upgrade check, an upgrade may fail due to compatibility issues. If this happens, perform a check again.
      -  If the upgrade check fails, you can click **View Report** on the **Upgrade Checks** tab page and rectify the incompatibility based on the report.

#. After the check is successful, click **Next**. Select "I understand Precautions for the Upgrade." and click **Upgrade Now**.
#. Specify **Cutover** and **Collect Statistics**.

   .. note::

      During a major version upgrade, optimizer statistics are not automatically synchronized. Statistics need to be collected after the upgrade is complete.

      -  **Before cutover**: Service stability is ensured. If your instance has a large amount of data, the upgrade may take a longer time.
      -  **After cutover**: Faster upgrade is ensured. After the upgrade, accessing tables that no statistics have been generated for may cause inaccurate execution plans and even instance breakdowns during peak hours.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
