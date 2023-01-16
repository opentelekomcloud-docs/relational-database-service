:original_name: rds_faq_0021.html

.. _rds_faq_0021:

What Should I Do If a Database Client Problem Causes a Connection Failure?
==========================================================================

Troubleshoot RDS connection failures caused by a client problem by checking the following items:

#. ECS Security Policy

   In Windows, check whether the RDS instance port is enabled in the Windows security policy. In Linux, run **iptables** to check whether the RDS DB instance port is enabled in firewall settings.

#. Application Configuration

   Check whether the connection address, port parameter configuration, and JDBC connection parameter configuration are correct.

#. Username or Password

   Check whether the username or password is correct if an error similar to the following occurs during RDS DB connection:

   -  [Warning] Access denied for user 'username'@'yourIp' (using password: NO)
   -  [Warning] Access denied for user 'username'@'yourIp' (using password: YES)
   -  Login failed for user 'username'

.. note::

   If the problem persists, contact post-sales technical support.
