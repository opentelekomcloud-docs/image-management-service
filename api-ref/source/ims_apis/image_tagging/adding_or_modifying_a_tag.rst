:original_name: en-us_topic_0067360381.html

.. _en-us_topic_0067360381:

Adding or Modifying a Tag
=========================

Function
--------

This API is used to add a tag to an image or modify a tag of an image. With tags, you can manage easily the images.

URI
---

PUT /v1/cloudimages/tags

Request
-------

-  Request parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================+
   | image_id        | Yes             | String          | Specifies the image ID.                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | For details about how to obtain the image ID, see :ref:`Querying Images <en-us_topic_0020091565>`.                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag             | No              | String          | Specifies the tag.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | Use either **tag** or **image_tag**.                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_tag       | No              | Object          | Lists the image tags. For detailed description, see :ref:`Image Tag Data Formats <en-us_topic_0020092110>`. This parameter is left blank by default. |
   |                 |                 |                 |                                                                                                                                                      |
   |                 |                 |                 | Use either **tag** or **image_tag**.                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 1** Data structure description of the image_tag field

      ========= ========= ====== ========================
      Parameter Mandatory Type   Description
      ========= ========= ====== ========================
      key       Yes       String Specifies the tag key.
      value     Yes       String Specifies the tag value.
      ========= ========= ====== ========================

-  Example request

   -  Example request containing parameter **tag**

      .. code-block:: text

         PUT https://{Endpoint}/v1/cloudimages/tags

      ::

         {
           "image_id": "62a15f6c-9197-44d2-89c7-708981c1bec1",
           "tag": "aaaa.1111"
         }

   -  Example request containing parameter **image_tag**

      .. code-block:: text

         PUT https://{Endpoint}/v1/cloudimages/tags

      ::

         {
           "image_id": "67437ebd-2563-46e0-887e-ad1923977fa1",
           "image_tag": {"key":"key1","value":"value1"}
         }

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
