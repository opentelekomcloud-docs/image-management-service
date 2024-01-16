:original_name: en-us_topic_0049147856.html

.. _en-us_topic_0049147856:

Replicating an Image Within a Region
====================================

Function
--------

This API is an extension one and is used to copy an existing image to another image. When replicating an image, you can change the image attributes to meet the requirements of different scenarios.

This API is an asynchronous one. If **job_id** is returned, the task is successfully delivered. You need to query the status of the asynchronous task. If the status is **success**, the task is successfully executed. If the status is **failed**, the task fails. For details about how to query the status of an asynchronous task, see :ref:`Querying the Status of an Asynchronous Job <en-us_topic_0022473688>`.

Constraints
-----------

-  Full-ECS images cannot be replicated.
-  Private images created using ISO files do not support in-region replication.

URI
---

POST /v1/cloudimages/{image_id}/copy

:ref:`Table 1 <en-us_topic_0049147856__table51065259105524>` lists the parameters in the URI.

.. _en-us_topic_0049147856__table51065259105524:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                        |
   +=================+=================+=================+====================================================================================================+
   | image_id        | Yes             | String          | Specifies the image ID.                                                                            |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | For details about how to obtain the image ID, see :ref:`Querying Images <en-us_topic_0020091565>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                             |
   +=======================+=================+=================+=========================================================================================================================================================================================================================================================================================================================================================+
   | name                  | Yes             | String          | Specifies the image name. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`.                                                                                                                                                                                                                        |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String          | Provides supplementary information about the image. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`. The value contains a maximum of 1024 characters and consists of only letters and digits. Carriage returns and angle brackets (< >) are not allowed. This parameter is left blank by default. |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cmk_id                | No              | String          | Specifies the encryption key. This parameter is left blank by default.                                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String          | Specifies the enterprise project that the image belongs to.                                                                                                                                                                                                                                                                                             |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                                                                         |
   |                       |                 |                 | -  If the value is **0** or left blank, the image belongs to the default enterprise project.                                                                                                                                                                                                                                                            |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                                                                         |
   |                       |                 |                 | -  If the value is a UUID, the image belongs to the enterprise project corresponding to the UUID.                                                                                                                                                                                                                                                       |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                                                                                         |
   |                       |                 |                 |    For more information about enterprise projects and how to obtain enterprise project IDs, see *Enterprise Management User Guide*.                                                                                                                                                                                                                     |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Replicating an image (name: ims_encrypted_copy3) within a region

.. code-block:: text

   POST https://{Endpoint}/v1/cloudimages/465076de-dc36-4aec-80f5-ef9d8009428f/copy
   {
       "name": "ims_encrypted_copy3",
       "description": "test copy",
       "cmk_id": "bd66288c-9081-460a-8227-4cbd0c814cb4"
   }

Response
--------

-  Response parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                  |
   +=======================+=======================+==============================================================================================+
   | job_id                | String                | Specifies the asynchronous job ID.                                                           |
   |                       |                       |                                                                                              |
   |                       |                       | For details, see :ref:`Querying the Status of an Asynchronous Job <en-us_topic_0022473688>`. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "job_id": "edc89b490d7d4392898e19b2deb34797"
      }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   +---------------------------+------------------------------------------------------------------------------+
   | Returned Value            | Description                                                                  |
   +===========================+==============================================================================+
   | 400 Bad Request           | Request error. For details, see :ref:`Error Codes <en-us_topic_0022473689>`. |
   +---------------------------+------------------------------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                                                       |
   +---------------------------+------------------------------------------------------------------------------+
   | 403 Forbidden             | You do not have the rights to perform the operation.                         |
   +---------------------------+------------------------------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                                        |
   +---------------------------+------------------------------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                                                      |
   +---------------------------+------------------------------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                                                  |
   +---------------------------+------------------------------------------------------------------------------+
