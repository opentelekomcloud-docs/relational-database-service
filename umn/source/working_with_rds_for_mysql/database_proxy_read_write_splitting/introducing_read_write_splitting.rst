:original_name: rds_11_0035.html

.. _rds_11_0035:

Introducing Read/Write Splitting
================================

Read/write splitting enables read and write requests to be automatically routed through a read/write splitting address. You can :ref:`enable read/write splitting <rds_11_0017>` after read replicas are created. Write requests are automatically routed to the primary DB instance and read requests are routed to read replicas by user-defined weights.

Proxy load balancing balances requests among multiple read replicas using a load-based scheduling policy. To enable proxy load balancing, contact customer service to apply for the required permissions.

Constraints
-----------

.. important::

   When read/write splitting is enabled, the system automatically deletes the existing account rdsProxy and creates a new rdsProxy account. When read/write splitting is disabled, the system automatically deletes the existing account rdsProxy. To prevent the system from deleting your created rdsProxy account, you are advised not to create it.

-  To use read/write splitting, connect to your DB instance through a private network because read/write splitting addresses are private IP addresses.
-  If you delete a primary DB instance after read/write splitting is enabled, the read replicas are also deleted and the read/write splitting function is disabled.
-  After read/write splitting is enabled, database ports, security groups, and floating IP addresses of both the primary DB instance and read replicas cannot be changed. If you do need to change any of them, change it before enabling read/write splitting.
-  Read/write splitting does not support SSL encryption.
-  Read/write splitting does not support the compression protocol.
-  Read/write splitting does not support the READ UNCOMMITTED transaction isolation level.
-  If multi-statements are executed, all subsequent requests will be routed to the primary DB instance. To restore the read/write splitting function, disconnect the connection from your applications and establish a connection again.
-  When read and write requests are split through the read/write splitting address, all transaction requests are routed to the primary DB instance while the non-transaction read consistency is not ensured. To ensure read consistency, encapsulate requests into transactions.
-  When the read/write splitting address is used, the LAST_INSERT_ID() function can be used only in transactions.
-  When the read/write splitting address is used, the execution results of the **show processlist** command are inconsistent.
-  When the read/write splitting address is used, the **show errors** and **show warnings** commands are not supported.
-  When the read/write splitting address is used, user-defined variables, such as the **SET @variable** statements, are not supported.
-  When the read/write splitting address is used, if stored procedures and functions depend on user variables (@variable), the execution result may be incorrect.
