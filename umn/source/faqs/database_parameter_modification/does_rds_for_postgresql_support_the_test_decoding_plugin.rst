:original_name: rds_faq_0119.html

.. _rds_faq_0119:

Does RDS for PostgreSQL Support the test_decoding Plugin?
=========================================================

PostgreSQL 10, PostgreSQL 11, PostgreSQL 12 and PostgreSQL 13 support test_decoding. For more information about test_decoding, see `test_decoding introduction <https://www.postgresql.org/docs/11/test-decoding.html>`__.

To use test_decoding, set **wal_level** to **logical**.

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target DB instance.
#. In the navigation pane on the left, choose **Parameters**. On the **Parameters** tab page, locate **wal_level** and change its value to **logical**.
#. Click **Save**. In the displayed dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
