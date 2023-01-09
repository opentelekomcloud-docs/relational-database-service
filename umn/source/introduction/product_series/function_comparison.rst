:original_name: rds_00_0011.html

.. _rds_00_0011:

Function Comparison
===================

Single DB instances use a single-node architecture. Different from the primary/standby DB instances, a single DB instance contains only one node and has no slave node for fault recovery.

Advantage Comparison
--------------------

-  Single DB instances: support the creation of read replicas (except for Microsoft SQL Server) and support the queries of error logs and slow query logs. Different from primary/standby DB instances that have two database nodes, a single DB instance has only one node. If a node fails, the restoration will take a long time. Therefore, single DB instances are not recommended for sensitive services that have high requirements on database availability.
-  Primary/Standby DB instances: use the slave database node only for failover and restoration. The slave database node does not provide services. The performance of single DB instances is similar to or even higher than the primary/standby DB instances.

.. _rds_00_0011__table1539112616503:

.. table:: **Table 1** Function comparisons

   +----------------------------------------+--------------------------------+--------------------------------+
   | Function                               | Single                         | Primary/Standby                |
   +========================================+================================+================================+
   | Number of nodes                        | 1                              | 2                              |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Specifications                         | vCPUs: a maximum of 60         | vCPUs: a maximum of 60         |
   |                                        |                                |                                |
   |                                        | Memory: a maximum of 512 GB    | Memory: a maximum of 512 GB    |
   |                                        |                                |                                |
   |                                        | Storage: a maximum of 4,000 GB | Storage: a maximum of 4,000 GB |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Monitoring and alarms                  | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Security group                         | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Backups and restorations               | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Recycle bin                            | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Parameter settings                     | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | SSL                                    | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Log management                         | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Read replicas (need to be created)     | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | High-frequency monitoring              | Supported                      | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Primary/standby switchover or failover | Not supported                  | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
   | Standby DB instance migration          | Not supported                  | Supported                      |
   +----------------------------------------+--------------------------------+--------------------------------+
