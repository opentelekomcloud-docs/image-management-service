:original_name: en-us_topic_0066978722.html

.. _en-us_topic_0066978722:

Deleting an Image (Native OpenStack API v1.1 - Abandoned and Not Recommended)
=============================================================================

Function
--------

This API is used to delete an image. If you soft delete the image with a specified ID, the image persists in the database, but in the **deleted** status.

This API has been discarded. :ref:`Deleting an Image (Native OpenStack API) <en-us_topic_0020092108>` is recommended.

URI
---

DELETE /v1.1/images/{image_id}

:ref:`Table 1 <en-us_topic_0066978722__table27262282>` lists the parameters in the URI.

.. _en-us_topic_0066978722__table27262282:

.. table:: **Table 1** Parameter description

   ========= ========= ====== =======================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================
   image_id  Yes       String Specifies the image ID.
   ========= ========= ====== =======================

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v1.1/images/3c3d1d01-b48a-4639-8a88-08be3b9b5d78

Response
--------

-  Response parameters

   None

-  Example response

   .. code-block:: text

      HTTP/1.1 200 OK

   ::

      Content-Type: text/html; charset=UTF-8
      Content-Length: 0
      X-Openstack-Request-Id: req-75e9edca-7b43-47da-bdc5-d39be469b72f
      Date: Mon, 23 May 2016 02:43:34 GMT

Returned Values
---------------

-  Normal

   204

-  Abnormal

   +---------------------------+------------------------------------------------------+
   | Returned Values           | Description                                          |
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
