:original_name: rds_faq_0018.html

.. _rds_faq_0018:

Can an External Server Access the RDS Database?
===============================================

DB Instance Bound with an EIP
-----------------------------

For a DB instance that has an EIP bound, you can access it through the EIP.

DB Instance Not Bound with an EIP
---------------------------------

-  Enable a VPN in a VPC and use the VPN to connect to the RDS DB instance.
-  Create an RDS and an ECS in the same VPC and access RDS through the ECS.
