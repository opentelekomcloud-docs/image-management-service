:original_name: en-us_topic_0049147877.html

.. _en-us_topic_0049147877:

Querying an Image Member List Schema (Native OpenStack API)
===========================================================

Function
--------

This API is used to query an image member list schema, which allows you to view image member attributes and their data types.

URI
---

GET /v2/schemas/members

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v2/schemas/members

Response
--------

-  Response parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                             |
   +=======================+=======================+=========================================================================================+
   | name                  | String                | Specifies the schema name.                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | links                 | Array of objects      | Specifies the URL for accessing the schema.                                             |
   |                       |                       |                                                                                         |
   |                       |                       | For details, see :ref:`Table 1 <en-us_topic_0049147877__table15641103183416>`.          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | properties            | Object                | Describes basic image attributes, including the type and usage of each attribute.       |
   |                       |                       |                                                                                         |
   |                       |                       | For details about the parameters, see :ref:`Image Attributes <en-us_topic_0020091562>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

   .. _en-us_topic_0049147877__table15641103183416:

   .. table:: **Table 1** Data structure description of the links field

      ========= ====== ======================================
      Parameter Type   Description
      ========= ====== ======================================
      href      String Specifies the domain name.
      rel       String Specifies the domain name description.
      ========= ====== ======================================

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "name": "members",
          "links": [
              {
                  "href": "{schema}",
                  "rel": "describedby"
              }
          ],
          "properties": {
              "members": {
                  "items": {
                      "name": "member",
                      "properties": {
                          "status": {
                              "enum": [
                                  "pending",
                                  "accepted",
                                  "rejected"
                              ],
                              "type": "string",
                              "description": "The status of this image member"
                          },
                          "created_at": {
                              "type": "string",
                              "description": "Date and time of image member creation"
                          },
                          "updated_at": {
                              "type": "string",
                              "description": "Date and time of last modification of image member"
                          },
                          "image_id": {
                              "pattern": "^([0-9a-fA-F]){8}-([0-9a-fA-F]){4}-([0-9a-fA-F]){4}-([0-9a-fA-F]){4}-([0-9a-fA-F]){12}$",
                              "type": "string",
                              "description": "An identifier for the image"
                          },
                          "member_id": {
                              "type": "string",
                              "description": "An identifier for the image member (tenantId)"
                          },
                          "schema": {
                              "readOnly": true,
                              "type": "string"
                          }
                      }
                  },
                  "type": "array"
              },
              "schema": {
                  "type": "string"
              }
          }
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
