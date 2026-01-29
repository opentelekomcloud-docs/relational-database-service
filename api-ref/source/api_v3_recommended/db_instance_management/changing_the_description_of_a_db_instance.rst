:original_name: rds_05_0029.html

.. _rds_05_0029:

Changing the Description of a DB Instance
=========================================

Function
--------

This API is used to change the description of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/alias

-  Parameter description

   .. table:: **Table 1** Parameter description

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

.. table:: **Table 3** Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                         |
   +=================+=================+=================+=====================================================================================================================+
   | alias           | No              | String          | The value consists of 0 to 64 characters, including letters, digits, periods (.), underscores (_), and hyphens (-). |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | If this parameter is not specified or is set to null, the original description of the instance will be deleted.     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Change the description of a DB instance.

.. code-block:: text

   PUT https://rds.eu-de.otc.t-systems.com/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/5b409baece064984a1b3eef6addae50cin01/alias

   {
        "alias": "alias-test"
   }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      ========= ====== =====================================================
      Parameter Type   Description
      ========= ====== =====================================================
      resp      String Returns **successful** if the invoking is successful.
      ========= ====== =====================================================

-  Example normal response

   .. code-block::

      {
          "resp": "successful"
      }

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
