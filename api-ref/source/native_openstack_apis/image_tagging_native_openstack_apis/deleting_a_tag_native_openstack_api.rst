:original_name: en-us_topic_0020091553.html

.. _en-us_topic_0020091553:

Deleting a Tag (Native OpenStack API)
=====================================

Function
--------

This API is used to delete a custom tag from a private image.

URI
---

DELETE /v2/images/{image_id}/tags/{tag}

:ref:`Table 1 <en-us_topic_0020091553__table25869170205722>` lists the parameters in the URI.

.. _en-us_topic_0020091553__table25869170205722:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                 |
   +=================+=================+=================+=============================================================================+
   | image_id        | Yes             | String          | Specifies the image ID.                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------+
   | tag             | Yes             | String          | Specifies the image tag.                                                    |
   |                 |                 |                 |                                                                             |
   |                 |                 |                 | The tag can contain only digits, letters, underscores (_), and hyphens (-). |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v2/images/4ca46bf1-5c61-48ff-b4f3-0ad4e5e3ba90/tags/aaaa

Response
--------

-  Response parameters

   None

-  Example response

   .. code-block:: text

      STATUS CODE 204

Returned Values
---------------

-  Normal

   204

-  Abnormal

   +---------------------------+------------------------------------------------------+
   | Returned Value            | Description                                          |
   +===========================+======================================================+
   | 400 Bad Request           | Request error.                                       |
   +---------------------------+------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                               |
   +---------------------------+------------------------------------------------------+
   | 403 Forbidden             | You do not have the rights to perform the operation. |
   +---------------------------+------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                |
   +---------------------------+------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                              |
   +---------------------------+------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                          |
   +---------------------------+------------------------------------------------------+
