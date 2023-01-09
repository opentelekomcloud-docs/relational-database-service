:original_name: rds_faq_0035.html

.. _rds_faq_0035:

Why Does the DB Instance Become Faulty After the Original Database Port Is Changed?
===================================================================================

Symptom
-------

-  The DB instance is in **Faulty** state after the original database port is changed.
-  The DB instance cannot be connected using the new database port.

Possible Causes
---------------

The submitted database port is occupied.

Procedure
---------

Change the database port to the new port again. For details, see :ref:`Changing a Database Port <rds_change_database_port>`.

-  If the database port is changed successfully, the previous change failed because the submitted database port was occupied.
-  If the original database port still fails to be changed, contact technical support.
