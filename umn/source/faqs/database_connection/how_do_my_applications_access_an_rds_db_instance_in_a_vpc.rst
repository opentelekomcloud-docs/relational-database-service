:original_name: rds_faq_0023.html

.. _rds_faq_0023:

How Do My Applications Access an RDS DB Instance in a VPC?
==========================================================

Ensure that the ECS in which your applications are located is in the same VPC as the RDS DB instance. If the ECS and the RDS DB instance are in different VPCs, modify the VPC route table and network access control list (ACL) to ensure that the ECS can access the RDS DB instance.
