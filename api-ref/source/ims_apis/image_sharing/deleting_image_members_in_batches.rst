:original_name: en-us_topic_0036994324.html

.. _en-us_topic_0036994324:

Deleting Image Members in Batches
=================================

Function
--------

This API is an extension one and used to stop sharing images by deleting tenants with whom the image is shared in batches.

This API is an asynchronous one. If **job_id** is returned, the task is successfully delivered. You need to query the status of the asynchronous task. If the status is **success**, the task is successfully executed. If the status is **failed**, the task fails. For details about how to query the status of an asynchronous task, see :ref:`Asynchronous Job Query <en-us_topic_0022473688>`.

URI
---

DELETE /v1/cloudimages/members

Request
-------

-  Request parameters

   ========= ========= ================ ==========================
   Parameter Mandatory Type             Description
   ========= ========= ================ ==========================
   images    Yes       Array of strings Specifies the image IDs.
   projects  Yes       Array of strings Specifies the project IDs.
   ========= ========= ================ ==========================

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v1/cloudimages/members

   ::

      {
        "images": [
              "d164b5df-1bc3-4c3f-893e-3e471fd16e64",
              "0b680482-acaa-4045-b14c-9a8c7dfe9c70"
        ],
        "projects": [
              "9c61004714024f9586705d090530f9fa",
              "edc89b490d7d4392898e19b2deb34797"
          ]
      }

Response
--------

-  Response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | job_id                | String                | Specifies the asynchronous task ID.                                      |
   |                       |                       |                                                                          |
   |                       |                       | For details, see :ref:`Asynchronous Job Query <en-us_topic_0022473688>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

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
