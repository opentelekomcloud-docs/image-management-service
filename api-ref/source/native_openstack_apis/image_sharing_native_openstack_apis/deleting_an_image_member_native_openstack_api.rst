:original_name: en-us_topic_0036994321.html

.. _en-us_topic_0036994321:

Deleting an Image Member (Native OpenStack API)
===============================================

Function
--------

This API is used to stop image sharing by deleting the tenant with whom the image is shared.

URI
---

DELETE /v2/images/{image_id}/members/{member_id}

:ref:`Table 1 <en-us_topic_0036994321__table6209770492526>` lists the parameters in the URI.

.. _en-us_topic_0036994321__table6209770492526:

.. table:: **Table 1** Parameter description

   ========= ========= ====== ========================
   Parameter Mandatory Type   Description
   ========= ========= ====== ========================
   image_id  Yes       String Specifies the image ID.
   member_id Yes       String Specifies the member ID.
   ========= ========= ====== ========================

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v2/images/d164b5df-1bc3-4c3f-893e-3e471fd16e64/members/edc89b490d7d4392898e19b2deb34797

Response
--------

-  Response parameters

   None

-  Example response

   .. code-block:: text

      204 No Content

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
