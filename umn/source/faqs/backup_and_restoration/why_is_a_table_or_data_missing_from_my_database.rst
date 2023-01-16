:original_name: rds_faq_0012.html

.. _rds_faq_0012:

Why Is a Table or Data Missing from My Database?
================================================

RDS does not delete or perform any operations on any user data. If this problem occurs, check if there have been any misoperations and restore the data from backup files, if necessary.

Check for misoperations: If the SQL audit function has been enabled, you can view data execution records in audit logs.

Restore data using backup files:

-  Use the RDS restoration function.
-  Import the backup data to RDS through an ECS.
