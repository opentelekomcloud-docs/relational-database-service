:original_name: rds_01_0004.html

.. _rds_01_0004:

High Security
=============

Network Isolation
-----------------

RDS uses Virtual Private Cloud (VPC) and network security groups to isolate and secure your DB instances. VPCs allow you to define what IP address range can access RDS. You can configure subnets and security groups to control access to DB instances.

Access Control
--------------

RDS controls access through the domain/IAM user and security groups. When you create an RDS DB instance, a domain is automatically created. To separate out specific permissions, you can create IAM users and assign permissions to them as needed. VPC security groups have rules that govern both inbound and outbound traffic for DB instances.

Transmission Encryption
-----------------------

RDS uses Transport Layer Security (TLS) and Secure Sockets Layer (SSL) to encrypt transmission. You can download a Certificate Agency (CA) certificate from the RDS console and upload it when connecting to a database for authentication.

Storage Encryption
------------------

RDS uses static encryption and tablespace encryption to encrypt the data to be stored. Encryption keys are managed by Key Management Service (KMS).

Data Deletion
-------------

When you delete an RDS DB instance, its attached disks, storage space its automated backups occupy, and all data it stores will be deleted. You can restore a deleted DB instance using a manual backup or rebuild the DB instance from the recycle bin within the retention period.

Anti-DDoS
---------

When you connect to an RDS DB instance through a public network, there may be risks of a distributed denial-of-service (DDoS) attack. If the RDS security system detects a DDoS attack, it will enable the anti-DDoS function. If the function cannot defend against the attack or the attack reaches the black hole threshold, black hole processing is triggered to ensure availability of the RDS service.

Security Protection
-------------------

RDS is protected by multiple layers of firewalls to defend against various malicious attacks, such as DDoS attacks and SQL injections. For security reasons, you are advised to access RDS through a private network.
