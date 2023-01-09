:original_name: rds_faq_0057.html

.. _rds_faq_0057:

How Can I Create and Connect to an ECS?
=======================================

#. For details about how to create an ECS, see the *Elastic Cloud Server User Guide*.

   -  If you connect to an RDS DB instance through a private network, ensure that the ECS and DB instance are in the same VPC. If you connect to an RDS DB instance through a public network, the ECS and DB instance can be in different VPCs.
   -  Configure a security group to allow the ECS to access the RDS DB instance through the IP address.

#. For details on how to connect to the ECS, see section "Logging In to an ECS" in the *Elastic Cloud Server User Guide*.
