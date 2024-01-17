:original_name: rds_faq_0051.html

.. _rds_faq_0051:

How Can I Identify the Validity Period of an SSL Root Certificate?
==================================================================

When you connect to an RDS MySQL DB instance using an SSL connection, run the following command to check whether the certificate has expired:

.. code-block::

   show status like '%ssl_server%';

Update the root certificate to the latest version before it expires:

#. In the **DB Information** area on the **Basic Information** page, click |image1| in the **SSL** field to download the root certificate or certificate bundle.
#. Reboot the DB instance for the new certificate to take effect.
#. Connect to the DB instance using the new certificate or certificate bundle.

   .. note::

      If a certificate is about to expire, replace it with an officially issued certificate to improve system security.

.. |image1| image:: /_static/images/en-us_image_0000001191211539.png
