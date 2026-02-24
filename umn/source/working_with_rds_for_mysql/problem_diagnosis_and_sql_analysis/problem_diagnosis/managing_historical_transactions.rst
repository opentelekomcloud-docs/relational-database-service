:original_name: rds_08_0039.html

.. _rds_08_0039:

Managing Historical Transactions
================================

Introduction
------------

This function is used to analyze and discover large transactions and the transactions that have been there for a long time without being committed in the database.

Data on historical transactions comes from the output of the **SHOW ENGINE INNODB STATUS** command. It shows the snapshot of historical transactions and is collected every 5 minutes.

Constraints
-----------

-  The snapshot of historical transactions only lists the transactions that are currently being executed. It does not include those that started and committed during a collection interval.
-  To collect historical transactions, enable **Collect Slow Query Logs** or **Collect All SQL Statements** first.
-  A maximum of 10,000 records generated in the past 7 days can be displayed.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.
#. On the **Instances** page, click the target instance name.
#. In the navigation pane, choose **DBA Assistant** > **Historical Diagnosis**.
#. Click the **Historical Transactions** tab.
#. In the upper part of the page, click **Log Settings**, enable **Collect Slow Query Logs** or **Collect All SQL Statements**, and click **OK**.
#. Enable **Collect Historical Transactions** and view historical transactions.

.. |image1| image:: /_static/images/en-us_image_0000001191211679.png
