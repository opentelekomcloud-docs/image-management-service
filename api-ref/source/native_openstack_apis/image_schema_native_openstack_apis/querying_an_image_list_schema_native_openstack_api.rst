:original_name: en-us_topic_0020091556.html

.. _en-us_topic_0020091556:

Querying an Image List Schema (Native OpenStack API)
====================================================

Function
--------

This API is used to query an image list schema, which allows you to know details about and the data structure of the image list.

URI
---

GET /v2/schemas/images

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v2/schemas/images

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
   |                       |                       | For details, see :ref:`Table 1 <en-us_topic_0020091556__table15641103183416>`.          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | properties            | Object                | Describes basic image attributes, including the type and usage of each attribute.       |
   |                       |                       |                                                                                         |
   |                       |                       | For details about the parameters, see :ref:`Image Attributes <en-us_topic_0020091562>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

   .. _en-us_topic_0020091556__table15641103183416:

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
          "name": "images",
          "links": [
              {
                  "href": "{first}",
                  "rel": "first"
              },
              {
                  "href": "{next}",
                  "rel": "next"
              },
              {
                  "href": "{schema}",
                  "rel": "describedby"
              }
          ],
          "properties": {
              "images": {
                  "items": {
                      "additionalProperties": {
                          "type": "String"
                      },
                      "name": "image",
                      "links": [
                          {
                              "href": "{self}",
                              "rel": "self"
                          },
                          {
                              "href": "{file}",
                              "rel": "enclosure"
                          },
                          {
                              "href": "{schema}",
                              "rel": "describedby"
                          }
                      ],
                      "properties": {
                          "status": {
                              "enum": [
                                  "queued",
                                  "saving",
                                  "active",
                                  "killed",
                                  "deleted",
                                  "pending_delete"
                              ],
                              "type": "string",
                              "description": "Status of the image (READ-ONLY)"
                          },
                          "tags": {
                              "items": {
                                  "type": "string",
                                  "maxLength": 255
                              },
                              "type": "array",
                              "description": "List of strings related to the image"
                          },
                          "kernel_id": {
                              "pattern": "^([0-9a-fA-F]){8}-([0-9a-fA-F]){4}-([0-9a-fA-F]){4}-([0-9a-fA-F]){4}-([0-9a-fA-F]){12}$",
                              "type": "string",
                              "description": "ID of image stored in Glance that should be used as the kernel when booting an AMI-style image.",
                              "is_base": false
                          },
                          "container_format": {
                              "enum": [
                                  "ami",
                                  "ari",
                                  "aki",
                                  "bare",
                                  "ovf",
                                  "ova"
                              ],
                              "type": "string",
                              "description": "Format of the container"
                          },
                          "min_ram": {
                              "type": "integer",
                              "description": "Amount of ram (in MB) required to boot image."
                          },
                          "ramdisk_id": {
                              "pattern": "^([0-9a-fA-F]){8}-([0-9a-fA-F]){4}-([0-9a-fA-F]){4}-([0-9a-fA-F]){4}-([0-9a-fA-F]){12}$",
                              "type": "string",
                              "description": "ID of image stored in Glance that should be used as the ramdisk when booting an AMI-style image.",
                              "is_base": false
                          },
                          "locations": {
                              "items": {
                                  "required": [
                                      "url",
                                      "metadata"
                                  ],
                                  "type": "object",
                                  "properties": {
                                      "url": {
                                          "type": "string",
                                          "maxLength": 255
                                      },
                                      "metadata": {
                                          "type": "object"
                                      }
                                  }
                              },
                              "type": "array",
                              "description": "A set of URLs to access the image file kept in external store"
                          },
                          "visibility": {
                              "enum": [
                                  "public",
                                  "private"
                              ],
                              "type": "string",
                              "description": "Scope of image accessibility"
                          },
                          "updated_at": {
                              "type": "string",
                              "description": "Date and time of the last image modification (READ-ONLY)"
                          },
                          "owner": {
                              "type": "string",
                              "description": "Owner of the image",
                              "maxLength": 255
                          },
                          "file": {
                              "type": "string",
                              "description": "(READ-ONLY)"
                          },
                          "min_disk": {
                              "type": "integer",
                              "description": "Amount of disk space (in GB) required to boot image."
                          },
                          "virtual_size": {
                              "type": "integer",
                              "description": "Virtual size of image in bytes (READ-ONLY)"
                          },
                          "id": {
                              "pattern": "^([0-9a-fA-F]){8}-([0-9a-fA-F]){4}-([0-9a-fA-F]){4}-([0-9a-fA-F]){4}-([0-9a-fA-F]){12}$",
                              "type": "string",
                              "description": "An identifier for the image"
                          },
                          "size": {
                              "type": "integer",
                              "description": "Size of image file in bytes (READ-ONLY)"
                          },
                          "instance_uuid": {
                              "type": "string",
                              "description": "ID of instance used to create this image.",
                              "is_base": false
                          },
                          "os_distro": {
                              "type": "string",
                              "description": "Common name of operating system distribution as specified in http://docs.openstack.org/trunk/openstack-compute/admin/content/adding-images.html",
                              "is_base": false
                          },
                          "name": {
                              "type": "string",
                              "description": "Descriptive name for the image",
                              "maxLength": 255
                          },
                          "checksum": {
                              "type": "string",
                              "description": "md5 hash of image contents. (READ-ONLY)",
                              "maxLength": 32
                          },
                          "created_at": {
                              "type": "string",
                              "description": "Date and time of image registration (READ-ONLY)"
                          },
                          "disk_format": {
                              "enum": [
                                  "ami",
                                  "ari",
                                  "aki",
                                  "vhd",
                                  "vmdk",
                                  "raw",
                                  "qcow2",
                                  "vdi",
                                  "iso"
                              ],
                              "type": "string",
                              "description": "Format of the disk"
                          },
                          "os_version": {
                              "type": "string",
                              "description": "Operating system version as specified by the distributor",
                              "is_base": false
                          },
                          "protected": {
                              "type": "boolean",
                              "description": "If true, image will not be deletable."
                          },
                          "architecture": {
                              "type": "string",
                              "description": "Operating system architecture as specified in http://docs.openstack.org/trunk/openstack-compute/admin/content/adding-images.html",
                              "is_base": false
                          },
                          "direct_url": {
                              "type": "string",
                              "description": "URL to access the image file kept in external store (READ-ONLY)"
                          },
                          "self": {
                              "type": "string",
                              "description": "(READ-ONLY)"
                          },
                          "schema": {
                              "type": "string",
                              "description": "(READ-ONLY)"
                          }
                      }
                  },
                  "type": "array"
              },
              "schema": {
                  "type": "string"
              },
              "next": {
                  "type": "string"
              },
              "first": {
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
