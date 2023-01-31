:original_name: en-us_topic_0093967372.html

.. _en-us_topic_0093967372:

Querying the Image Quota
========================

Function
--------

This extension API is used to query the quota of private images of a tenant in the current region.

URI
---

GET /v1/cloudimages/quota

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v1/cloudimages/quota

Response
--------

-  Response parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                  |
   +=======================+=======================+==============================================================================+
   | quotas                | Object                | Specifies the quota information.                                             |
   |                       |                       |                                                                              |
   |                       |                       | For details, see :ref:`Table 1 <en-us_topic_0093967372__table147763014020>`. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+

   .. _en-us_topic_0093967372__table147763014020:

   .. table:: **Table 1** Data structure description of the quotas field

      +-----------------------+-----------------------+-----------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                 |
      +=======================+=======================+=============================================================================+
      | resources             | Array of objects      | Specifies the images included in the quota.                                 |
      |                       |                       |                                                                             |
      |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0093967372__table29581211801>`. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------+

   .. _en-us_topic_0093967372__table29581211801:

   .. table:: **Table 2** Data structure description of the quotas.resources field

      ========= ======= =================================================
      Parameter Type    Description
      ========= ======= =================================================
      type      String  Specifies the type of the resource to be queried.
      used      Integer Specifies the used quota.
      quota     Integer Specifies the total quota.
      min       Integer Specifies the minimum quota.
      max       Integer Specifies the maximum quota.
      ========= ======= =================================================

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
        "quotas": {
          "resources": [
            {
              "type": "image",
              "used": 0,
              "quota": 20,
              "min": 1,
              "max": 1000
            }
          ]
        }
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
