:original_name: en-us_topic_0020092111.html

.. _en-us_topic_0020092111:

Adding a Tag (Native OpenStack API)
===================================

Function
--------

This API is used to add a custom tag to an image. With tags, you can manage easily the images.

URI
---

PUT /v2/images/{image_id}/tags/{tag}

:ref:`Table 1 <en-us_topic_0020092111__table58396974>` lists the parameters in the URI.

.. _en-us_topic_0020092111__table58396974:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================+
   | image_id        | Yes             | String          | Specifies the image ID.                                                                                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag             | Yes             | String          | Specifies the tag to be added.                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | The tag can contain only digits, letters, underscores (_), and hyphens (-).                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | .. note::                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 |    This API can only be used to add a tag key. To add a tag value, use the PUT /v1/cloudimages/tags API. For details, see :ref:`Adding or Modifying a Tag <en-us_topic_0067360381>`. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

Request parameters

None

Example Request
---------------

Adding an image tag

.. code-block:: text

   PUT https://{Endpoint}/v2/images/4ca46bf1-5c61-48ff-b4f3-0ad4e5e3ba90/tags/aaaa

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
