:original_name: en-us_topic_0036994322.html

.. _en-us_topic_0036994322:

Adding Image Recipients
=======================

Function
--------

This is an extended API used to share more than one image with multiple users.

This is an asynchronous API. If **job_id** is returned, the job is successfully delivered. You need to query the status of the asynchronous job. If the status is **success**, the job is successfully executed. If the status is **failed**, the job fails. For details about how to query an asynchronous job, see :ref:`Querying the Progress of an Asynchronous Job <en-us_topic_0000001263414852>`.

Constraints
-----------

For encrypted images, you need to authorize the keys used by the images before you use this API. For details, see "How Do I Authorize a Key?" in *Image Management Service User Guide*.

URI
---

POST /v1/cloudimages/members

Request
-------

-  Request parameters

   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                            |
   +=================+=================+==================+========================================================================================================================+
   | images          | Yes             | Array of strings | **Definition**                                                                                                         |
   |                 |                 |                  |                                                                                                                        |
   |                 |                 |                  | Image IDs.                                                                                                             |
   |                 |                 |                  |                                                                                                                        |
   |                 |                 |                  | **Constraints**                                                                                                        |
   |                 |                 |                  |                                                                                                                        |
   |                 |                 |                  | N/A                                                                                                                    |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | projects        | Yes             | Array of strings | **Definition**                                                                                                         |
   |                 |                 |                  |                                                                                                                        |
   |                 |                 |                  | Project IDs. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <en-us_topic_0121673684>`. |
   |                 |                 |                  |                                                                                                                        |
   |                 |                 |                  | **Constraints**                                                                                                        |
   |                 |                 |                  |                                                                                                                        |
   |                 |                 |                  | At least one of **projects**, **domains**, or **organizations** must be specified.                                     |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Adding tenants who can use shared images (image IDs: d164b5df-1bc3-4c3f-893e-3e471fd16e64, 0b680482-acaa-4045-b14c-9a8c7dfe9c70; project IDs: 9c61004714024f9586705d090530f9fa, edc89b490d7d4392898e19b2deb34797)

.. code-block:: text

   POST https://{Endpoint}/v1/cloudimages/members
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
