:original_name: en-us_topic_0049147856.html

.. _en-us_topic_0049147856:

Replicating an Image Within a Region
====================================

Function
--------

This is an extended API used to replicate an image. When replicating an image, you can change the image attributes to meet the requirements of different scenarios.

This is an asynchronous API. If **job_id** is returned, the job is successfully delivered. You need to query the status of the asynchronous job. If the status is **success**, the job is successfully executed. If the status is **failed**, the job fails. For details about how to query an asynchronous job, see :ref:`Querying the Progress of an Asynchronous Job <en-us_topic_0000001263414852>`.

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

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                 |
   +=================+=================+=================+=============================================================================================================+
   | image_id        | Yes             | String          | **Definition**                                                                                              |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | Image ID. For details about how to obtain an image ID, see :ref:`Querying Images <en-us_topic_0020091565>`. |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | **Constraints**                                                                                             |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | N/A                                                                                                         |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | **Range**                                                                                                   |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | N/A                                                                                                         |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | **Default Value**                                                                                           |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | N/A                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                                                                                                                    |
   +=======================+=================+=================+================================================================================================================================================================================================================================================+
   | name                  | Yes             | String          | **Definition**                                                                                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | Image name. For details about **name**, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`.                                                                                                                           |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Constraints**                                                                                                                                                                                                                                |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | A name cannot start or end with a space.                                                                                                                                                                                                       |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Range**                                                                                                                                                                                                                                      |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | A name can contain only letters, digits, spaces, hyphens (-), underscores (_), and periods (.), and cannot start or end with a space. The name length must be 1 to 128 characters.                                                             |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Default Value**                                                                                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | N/A                                                                                                                                                                                                                                            |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String          | **Definition**                                                                                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | Image description. For details about **description**, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`.                                                                                                             |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Constraints**                                                                                                                                                                                                                                |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | N/A                                                                                                                                                                                                                                            |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Range**                                                                                                                                                                                                                                      |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | The value contains a maximum of 1,024 characters, including letters and digits. Carriage returns and angle brackets (< >) are not allowed.                                                                                                     |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Default Value**                                                                                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | N/A                                                                                                                                                                                                                                            |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cmk_id                | No              | String          | **Definition**                                                                                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | Encryption key. Enter the ID of the KMS Customer Master Key (CMK) used to encrypt the image. This parameter is mandatory when you create an encrypted image.                                                                                   |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Constraints**                                                                                                                                                                                                                                |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | N/A                                                                                                                                                                                                                                            |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Range**                                                                                                                                                                                                                                      |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | N/A                                                                                                                                                                                                                                            |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Default Value**                                                                                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | This parameter is left blank by default.                                                                                                                                                                                                       |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String          | **Definition**                                                                                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | Enterprise project that an image belongs to.                                                                                                                                                                                                   |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | For more information about enterprise projects and how to obtain enterprise project IDs, see `Enterprise Project Service User Guide <https://docs.otc.t-systems.com/enterprise-project-service/umn/#enterprise-project-service-user-guide>`__. |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Constraints**                                                                                                                                                                                                                                |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | If only enterprise project authorization is used, the **enterprise_project_id** parameter must be specified. Otherwise, an error may occur, indicating that you do not have the required permissions.                                          |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Range**                                                                                                                                                                                                                                      |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | -  If the value is **0** or left blank, an image belongs to the **default** enterprise project.                                                                                                                                                |
   |                       |                 |                 | -  If the value is a UUID, an image belongs to the enterprise project with this UUID.                                                                                                                                                          |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | **Default Value**                                                                                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                                                                                |
   |                       |                 |                 | N/A                                                                                                                                                                                                                                            |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                          |
   +=======================+=======================+======================================================================================================+
   | job_id                | String                | **Definition**                                                                                       |
   |                       |                       |                                                                                                      |
   |                       |                       | Asynchronous job ID.                                                                                 |
   |                       |                       |                                                                                                      |
   |                       |                       | For details, see :ref:`Querying the Progress of an Asynchronous Job <en-us_topic_0000001263414852>`. |
   |                       |                       |                                                                                                      |
   |                       |                       | **Range**                                                                                            |
   |                       |                       |                                                                                                      |
   |                       |                       | N/A                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+

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
   | 403 Forbidden             | Insufficient permissions.                                                    |
   +---------------------------+------------------------------------------------------------------------------+
   | 404 Not Found             | Requested resource not found.                                                |
   +---------------------------+------------------------------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                                                      |
   +---------------------------+------------------------------------------------------------------------------+
   | 503 Service Unavailable   | Service unavailable.                                                         |
   +---------------------------+------------------------------------------------------------------------------+
