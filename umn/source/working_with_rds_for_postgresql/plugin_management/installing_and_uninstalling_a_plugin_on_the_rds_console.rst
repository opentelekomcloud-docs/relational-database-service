:original_name: rds_09_0070.html

.. _rds_09_0070:

Installing and Uninstalling a Plugin on the RDS Console
=======================================================

Scenarios
---------

RDS allows you to install and uninstall plugins on the console.

RDS for PostgreSQL plugins only take effect on the databases you created the plugins for. To use a plugin on databases, it has to be created separately for each database.

Prerequisites
-------------

Before installing or uninstalling plugins, ensure that there are databases in your instance.

Precautions
-----------

-  plpgsql is a built-in plugin and cannot be uninstalled.
-  Logical replication plugins, such as decoderbufs and wal2json, can be used as-is. There is no installation required.
-  Some plugins depend on the **shared_preload_libraries** parameter. They can be installed only after related libraries are loaded.
-  pg_cron is only available to RDS for PostgreSQL 12 (12.11.0 and later), 13, and 14. Before using this plugin, change the value of **cron.database_name** to the name of the database this plugin is used for (only one database is supported), and change the value of **cron.use_background_workers** to **on**.
-  pltcl is not supported for RDS for PostgreSQL 13.2. To use this plugin, upgrade your instance to the latest minor version.
-  Installing or uninstalling some plugins will cause their dependent plugins and tables to be installed or uninstalled synchronously. For example, when you install or uninstall postgis, postgis_sfcgal will be installed or uninstalled at the same time.

Modifying the **shared_preload_libraries** Parameter
----------------------------------------------------

Some plugins require corresponding parameter values to be loaded before the plugins can be installed.

You can modify the **shared_preload_libraries** parameter to load parameter values in batches or load each required parameter value independently before installing a plugin.

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **Plugins**.
#. On the **Plugins** page, click |image2| next to **Loaded shared_preload_libraries parameter values** to view the loaded parameter values.
#. Click **Modify Parameter Values**.
#. Select the parameter values to be loaded from the drop-down list box and click **OK**.
#. In the displayed dialog box, click **OK**.

   .. note::

      -  The modified parameter values take effect only after the instance is rebooted. If your instance has read replicas, the parameter values for the read replicas are also modified. You also need to reboot the read replicas.
      -  To ensure security and O&M functions of RDS for PostgreSQL, the following parameter values are loaded by default and cannot be deleted:

         -  **passwordcheck.so**
         -  **pg_stat_statements**
         -  **pg_sql_history**
         -  **pgaudit**

#. You can also load each parameter value independently before installing a plugin.

Installing and Uninstalling a Plugin
------------------------------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region.
#. Click **Service List**. Under **Database**, click **Relational Database Service**.
#. On the **Instances** page, click the instance name.
#. In the navigation pane, choose **Plugins**.
#. In the **Database** drop-down list above the plugin list, select the database where the plugin is to be installed.
#. Locate the plugin to be installed and click **Install** in the **Operation** column.
#. To uninstall a plugin, click **Uninstall**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
.. |image2| image:: /_static/images/en-us_image_0000001841634206.png
.. |image3| image:: /_static/images/en-us_image_0000001633304538.png
