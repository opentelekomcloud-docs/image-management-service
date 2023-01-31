:original_name: en-us_topic_0066978721.html

.. _en-us_topic_0066978721:

Querying Image Metadata (Native OpenStack API v1 - Abandoned and Not Recommended)
=================================================================================

Function
--------

This API is used to query image metadata.

This API has been discarded. The API for querying image details (:ref:`Querying Image Details (Native OpenStack API) <en-us_topic_0020091566>`) is recommended.

URI
---

HEAD /v1/images/{image_id}

:ref:`Table 1 <en-us_topic_0066978721__table27262282>` lists the parameters in the URI.

.. _en-us_topic_0066978721__table27262282:

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

      HEAD https://{Endpoint}/v1/images/3c3d1d01-b48a-4639-8a88-08be3b9b5d78

Response
--------

-  Response parameters

   +------------------+---------+--------------------------------------------------------------------------------------+
   | Parameter        | Type    | Description                                                                          |
   +==================+=========+======================================================================================+
   | Status           | String  | Image status                                                                         |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Virtual_size     | Integer | Virtual size of an image                                                             |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Name             | String  | Image name                                                                           |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Deleted          | Boolean | Whether an image has been deleted                                                    |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Container_format | String  | Image container type                                                                 |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Created_at       | String  | Time when an image was created                                                       |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Disk_format      | String  | Image file type                                                                      |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Updated_at       | String  | Time when an image was updated                                                       |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Property         | Object  | Image attribute                                                                      |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Owner            | String  | Tenant to which an image belongs                                                     |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Protected        | Boolean | Whether an image is protected                                                        |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Min_ram          | Integer | Minimum memory (MB) required for running an image                                    |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Checksum         | String  | Image verification sum. This parameter is available after an image file is uploaded. |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Min_disk         | Integer | Minimum disk capacity (GB) required for running the image                            |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Is_public        | Boolean | Whether an image is a public one                                                     |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Deleted_at       | String  | Time when an image was deleted                                                       |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Id               | String  | Image UUID                                                                           |
   +------------------+---------+--------------------------------------------------------------------------------------+
   | Size             | Integer | Image size. This parameter is available after an image file is uploaded.             |
   +------------------+---------+--------------------------------------------------------------------------------------+

   These parameters are contained in the header of the HTTP response message.

-  Example response

   .. code-block:: text

      HTTP/1.1 200 OK

   ::

      Content-Type: text/html; charset=UTF-8
      Content-Length: 0
      X-Image-Meta-Id: 3c3d1d01-b48a-4639-8a88-08be3b9b5d78
      X-Image-Meta-Deleted: False
      X-Image-Meta-Container_format: bare
      X-Image-Meta-Checksum: 64d7c1cd2b6f60c92c14662941cb7913
      X-Image-Meta-Protected: False
      X-Image-Meta-Min_disk: 0
      X-Image-Meta-Created_at: 2016-05-22T06:04:20.425843
      X-Image-Meta-Size: 13167616
      X-Image-Meta-Status: active
      X-Image-Meta-Is_public: True
      X-Image-Meta-Min_ram: 0
      X-Image-Meta-Owner: 23f4cb75768d4febb39542ef6fe169f3
      X-Image-Meta-Updated_at: 2016-05-22T06:04:22.719791
      X-Image-Meta-Disk_format: qcow2
      X-Image-Meta-Name: cirros
      Etag: 64d7c1cd2b6f60c92c14662941cb7913
      X-Openstack-Request-Id: req-7123ca83-da23-4f4e-9ed6-accd3707d333
      Date: Mon, 23 May 2016 02:29:54 GMT

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
