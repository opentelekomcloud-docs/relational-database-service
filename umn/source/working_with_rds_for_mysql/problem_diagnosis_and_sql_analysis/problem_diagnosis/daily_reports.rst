:original_name: rds_08_0035.html

.. _rds_08_0035:

Daily Reports
=============

Scenarios
---------

You can start a diagnosis for your DB instance and subscribe to diagnosis reports.

-  :ref:`Starting a Diagnosis <rds_08_0035__en-us_topic_0000001373048845_section195706267423>`: You can perform an overall health diagnosis on your instance and view details of the current and historical diagnosis reports.
-  :ref:`Subscribing to Diagnosis Reports <rds_08_0035__section1277716344571>`: Simple Message Notification (SMN) can send diagnosis exception reports to the preset email address so that you can learn about the overall health status of your instance in real time.

.. _rds_08_0035__en-us_topic_0000001373048845_section195706267423:

Starting a Diagnosis
--------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the DB instance name.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Click the **Daily Reports** tab.
#. Click **Start Diagnosis**. Select a time range for the diagnosis. The time span is within one day.

   .. note::

      If you want to be notified of risks through email, see :ref:`Subscribing to Diagnosis Reports <rds_08_0035__section1277716344571>`.

#. In the **Diagnosis Dimensions** area, click **Slow SQL Analysis**, **All SQL Analysis**, or **Performance & Storage** to view diagnosis report details.
#. You can also view historical diagnosis reports or download a report to your local PC.

   -  To view historical diagnosis reports, click **View History** in the upper right corner of the page.
   -  To download a report to your local PC, click **Download** in the upper right corner of the page.

.. _rds_08_0035__section1277716344571:

Subscribing to Diagnosis Reports
--------------------------------

#. On the **Instances** page, click the DB instance name.

#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.

#. Click the **Daily Reports** tab.

#. In the upper right corner of the page, click **Subscribe** and set subscription parameters. For details about the parameters, see :ref:`Table 1 <rds_08_0035__table15405957124920>`.


   .. figure:: /_static/images/en-us_image_0000002378668778.png
      :alt: **Figure 1** Subscribe to Daily Report

      **Figure 1** Subscribe to Daily Report

   .. _rds_08_0035__table15405957124920:

   .. table:: **Table 1** Subscription parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================+
      | Subscription                      | Select **By topic** or **By email**.                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topics                            | A topic is used to publish messages and subscribe to notifications. It serves as a message transmission channel between publishers and subscribers.                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Email Addresses                   | If you select **By email** for **Subscription**, you need to specify **Email Addresses**.                                                                                                                        |
      |                                   |                                                                                                                                                                                                                  |
      |                                   | An email will be sent to the specified email address only when risks are identified after a diagnosis is performed. You can enter up to 15 email addresses and separate each email address with a semicolon (;). |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. If you want to unsubscribe from diagnosis reports, click **Unsubscribe** in the upper right corner of the page. In the displayed dialog box, confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
