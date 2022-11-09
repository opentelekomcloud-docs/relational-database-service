:original_name: en-us_topic_0032488197.html

.. _en-us_topic_0032488197:

Abnormal Request Results
========================

v3 APIs
-------

**Abnormal response description**

.. table:: **Table 1** Abnormal response description

   +------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name       | Type   | Description                                                                                                                                                             |
   +============+========+=========================================================================================================================================================================+
   | error_code | String | Specifies the error code returned when a task submission exception occurs. For details, see :ref:`Table 2 <en-us_topic_0032488241__td93aca0e44834bb3939478d798feb72e>`. |
   +------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_msg  | String | Specifies the description of the error returned when a task submission exception occurs.                                                                                |
   +------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Response example**

.. code-block:: text

   {
       "error_code": "DBS.200022",
       "error_msg": "The DB instance name already exists."
   }

v1 APIs
-------

**Abnormal response description**

.. table:: **Table 2** Abnormal response description

   +-----------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Type   | Description                                                                                                                                                             |
   +=================+========+=========================================================================================================================================================================+
   | errCode         | String | Specifies the error code returned when a task submission exception occurs. For details, see :ref:`Table 2 <en-us_topic_0032488241__td93aca0e44834bb3939478d798feb72e>`. |
   +-----------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | externalMessage | String | Specifies the description of the error returned when a task submission exception occurs.                                                                                |
   +-----------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Response example**

.. code-block:: text

   {
       "errCode": "RDS.1102",
       "externalMessage": "The DB instance name already exists."
   }

OpenStack Trove API v1.0 APIs
-----------------------------

**Abnormal response description**

.. table:: **Table 3** Abnormal response description (using itemNotFound as an example)

   +--------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name         | Type                                                                                               | Description                                                                                                                                      |
   +==============+====================================================================================================+==================================================================================================================================================+
   | itemNotFound | List data structure. For details, see :ref:`Table 4 <en-us_topic_0032488197__table6204277318822>`. | Specifies the error type when a task submission exception occurs. For details, see :ref:`Table 3 <en-us_topic_0032488241__table57182163211057>`. |
   +--------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0032488197__table6204277318822:

.. table:: **Table 4** Error type parameter data structure description

   +---------+--------+------------------------------------------------------------------------------------------+
   | Name    | Type   | Description                                                                              |
   +=========+========+==========================================================================================+
   | code    | String | Specifies the response code returned when a task submission exception occurs.            |
   +---------+--------+------------------------------------------------------------------------------------------+
   | message | String | Specifies the description of the error returned when a task submission exception occurs. |
   +---------+--------+------------------------------------------------------------------------------------------+

**Response example**

.. code-block:: text

   {
     "itemNotFound": {
       "code": 404,
       "message": "The resource could not be found."
     }
   }
