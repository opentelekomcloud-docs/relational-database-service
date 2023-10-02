:original_name: rds_pg_07_0003.html

.. _rds_pg_07_0003:

RDS Custom Policies
===================

Custom policies can be created to supplement the system policies of RDS.

You can create custom policies in either of the following two ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions without the need to know policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/usermanual/iam/en-us_topic_0274187246.html>`__. The following section contains examples of common RDS custom policies.

Example Custom Policies
-----------------------

-  Example 1: Allowing users to create RDS DB instances

   .. code-block:: text

      {
          "Version": "1.1",
          "Statement": [{
              "Effect": "Allow",
              "Action": ["rds:instance:create"]
          }]
      }

-  Example 2: Denying RDS DB instance deletion

   A policy with only "Deny" permissions must be used in conjunction with other policies to take effect. If the permissions assigned to a user include both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **RDS FullAccess** policy to a user but you want to prevent the user from deleting RDS DB instances. Create a custom policy for denying RDS DB instance deletion, and attach both policies to the group the user belongs to. Then, the user can perform all operations on RDS DB instances except deleting RDS DB instances. The following is an example deny policy:

   .. code-block:: text

      {
          "Version": "1.1",
          "Statement": [{
              "Action": ["rds:instance:delete"],
              "Effect": "Deny"
          }]
      }
