:original_name: en-us_topic_0036994320.html

.. _en-us_topic_0036994320:

Querying Image Members (Native OpenStack API)
=============================================

Function
--------

This API is used to query the tenants with whom an image is shared using search criteria and to display the tenants in a list.

URI
---

GET /v2/images/{image_id}/members

:ref:`Table 1 <en-us_topic_0036994320__table27262282>` lists the parameters in the URI.

.. _en-us_topic_0036994320__table27262282:

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

      GET https://{Endpoint}/v2/images/d164b5df-1bc3-4c3f-893e-3e471fd16e64/members

Response
--------

-  Response parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                 |
   +=======================+=======================+=============================================================================+
   | members               | Array of objects      | Specifies the members.                                                      |
   |                       |                       |                                                                             |
   |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0036994320__table47745347163>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------+
   | schema                | String                | Specifies the sharing schema.                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------+

   .. _en-us_topic_0036994320__table47745347163:

   .. table:: **Table 2** Data structure description of the members field

      +------------+--------+---------------------------------------------------------------------------------+
      | Parameter  | Type   | Description                                                                     |
      +============+========+=================================================================================+
      | status     | String | Specifies the image sharing status.                                             |
      +------------+--------+---------------------------------------------------------------------------------+
      | created_at | String | Specifies the time when a shared image was created. The value is in UTC format. |
      +------------+--------+---------------------------------------------------------------------------------+
      | updated_at | String | Specifies the time when a shared image was updated. The value is in UTC format. |
      +------------+--------+---------------------------------------------------------------------------------+
      | image_id   | String | Specifies the image ID.                                                         |
      +------------+--------+---------------------------------------------------------------------------------+
      | member_id  | String | Specifies the member ID.                                                        |
      +------------+--------+---------------------------------------------------------------------------------+
      | schema     | String | Specifies the sharing schema.                                                   |
      +------------+--------+---------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "members": [
              {
                  "status": "accepted",
                  "created_at": "2016-09-01T02:05:14Z",
                  "updated_at": "2016-09-01T02:37:11Z",
                  "image_id": "d164b5df-1bc3-4c3f-893e-3e471fd16e64",
                  "member_id": "edc89b490d7d4392898e19b2deb34797",
                  "schema": "/v2/schemas/member"
              }
          ],
          "schema": "/v2/schemas/members"
      }

Returned Values
---------------

-  Normal

   200

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
