:original_name: en-us_topic_0000001411479505.html

.. _en-us_topic_0000001411479505:

Replicating an Image Within a Region
====================================

Function
--------

This API is an extension one and is used to copy an existing image to another image. When replicating an image, you can change the image attributes to meet the requirements of different scenarios.

This API is an asynchronous one. If **job_id** is returned, the task is successfully delivered. You need to query the status of the asynchronous task. If the status is **success**, the task is successfully executed. If the status is **failed**, the task fails. For details about how to query the status of an asynchronous task, see :ref:`Asynchronous Job Query <en-us_topic_0000001361199224>`.

Constraints
-----------

-  Full-ECS images cannot be replicated.

URI
---

POST /v1/cloudimages/{image_id}/copy

:ref:`Table 1 <en-us_topic_0000001411479505__table51065259105524>` lists the parameters in the URI.

.. _en-us_topic_0000001411479505__table51065259105524:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                              |
   +=================+=================+=================+==========================================================================================================+
   | image_id        | Yes             | String          | Specifies the image ID.                                                                                  |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | For details about how to obtain the image ID, see :ref:`Querying Images <en-us_topic_0000001360879728>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                   |
   +=============+===========+========+===============================================================================================================================================================================================================================================================================================================================================================+
   | name        | Yes       | String | Specifies the image name. For detailed description, see :ref:`Image Attributes <en-us_topic_0000001361199252__section61598810155254>`.                                                                                                                                                                                                                        |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | No        | String | Provides supplementary information about the image. For detailed description, see :ref:`Image Attributes <en-us_topic_0000001361199252__section61598810155254>`. The value contains a maximum of 1024 characters and consists of only letters and digits. Carriage returns and angle brackets (< >) are not allowed. This parameter is left blank by default. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cmk_id      | No        | String | Specifies the encryption key. This parameter is left blank by default.                                                                                                                                                                                                                                                                                        |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{Endpoint}/v1/cloudimages/465076de-dc36-4aec-80f5-ef9d8009428f/copy

   ::

      {
          "name": "ims_encrypted_copy3",
          "description": "test copy",
          "cmk_id": "bd66288c-9081-460a-8227-4cbd0c814cb4"
      }

Response
--------

-  Response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                    |
   +=======================+=======================+================================================================================+
   | job_id                | String                | Specifies the asynchronous job ID.                                             |
   |                       |                       |                                                                                |
   |                       |                       | For details, see :ref:`Asynchronous Job Query <en-us_topic_0000001361199224>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "job_id": "edc89b490d7d4392898e19b2deb34797"
      }

Returned Value
--------------

-  Normal

   200

-  Abnormal

   +---------------------------+------------------------------------------------------------------------------------+
   | Returned Value            | Description                                                                        |
   +===========================+====================================================================================+
   | 400 Bad Request           | Request error. For details, see :ref:`Error Codes <en-us_topic_0000001411239233>`. |
   +---------------------------+------------------------------------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                                                             |
   +---------------------------+------------------------------------------------------------------------------------+
   | 403 Forbidden             | You do not have the rights to perform the operation.                               |
   +---------------------------+------------------------------------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                                              |
   +---------------------------+------------------------------------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                                                            |
   +---------------------------+------------------------------------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                                                        |
   +---------------------------+------------------------------------------------------------------------------------+
