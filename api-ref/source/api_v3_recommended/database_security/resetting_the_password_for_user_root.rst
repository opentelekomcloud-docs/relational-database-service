:original_name: rds_05_0011.html

.. _rds_05_0011:

Resetting the Password for User Root
====================================

Function
--------

This API is used to reset the password if you forget the password of your database account when using RDS. If an error occurs on the root account, for example, the root account is lost or deleted, you can restore the root account rights through resetting the password.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

The password cannot be reset if the DB instance is in any of the following statuses: creating, rebooting, upgrading, changing instance class, creating users, or deleting users.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/password

-  Parameter description

   .. table:: **Table 1** URI Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | Content-Type    | Yes             | String          | The content type.                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The default value is **application/json**.                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Request body parameters

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                        |
      +=================+=================+=================+====================================================================================================================================================================================================================+
      | db_user_pwd     | Yes             | String          | Specifies the database password. Valid value (for all RDS engines):                                                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                                                                    |
      |                 |                 |                 | The value must be 8 to 32 characters long and contain at least three types of the following characters: uppercase letters, lowercase letters, digits, and special characters (:literal:`\``~!@#$%^*-_=+?,()&`\``). |
      |                 |                 |                 |                                                                                                                                                                                                                    |
      |                 |                 |                 | .. important::                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                    |
      |                 |                 |                 |    NOTICE:                                                                                                                                                                                                         |
      |                 |                 |                 |    You are advised to enter a strong password to improve security, preventing security risks such as brute force cracking.                                                                                         |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Reset the password for user **root**.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/password

   {
        "db_user_pwd": "******"
   }

Response
--------

-  Normal response

   None

-  Example normal response

   .. code-block::

      {}

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
