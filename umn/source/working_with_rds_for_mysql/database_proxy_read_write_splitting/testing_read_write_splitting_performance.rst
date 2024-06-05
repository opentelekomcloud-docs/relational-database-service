:original_name: rds_11_0021.html

.. _rds_11_0021:

Testing Read/Write Splitting Performance
========================================

After read/write splitting is enabled, databases can be connected through a read/write splitting address. You can use internal SQL commands to verify the read/write splitting performance.

Procedure
---------

#. Connect to a database through a read/write splitting address by referring to :ref:`Enabling Read/Write Splitting <rds_11_0017>`.

#. Run **show last route** to view the routing result of the previous SQL statement.


   .. figure:: /_static/images/en-us_image_0000001533364489.png
      :alt: **Figure 1** Query result

      **Figure 1** Query result

   Do not use **show last route** for service code or include it in multi-statements.
