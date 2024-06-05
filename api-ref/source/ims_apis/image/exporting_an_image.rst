:original_name: en-us_topic_0036994315.html

.. _en-us_topic_0036994315:

Exporting an Image
==================

Function
--------

This is an extension API and used to export a private image to an OBS bucket.

.. note::

   Before exporting an image, ensure that you have the Tenant Administrator permission for OBS.

Constraints
-----------

-  An image can only be exported to a Standard bucket that is in the same region as the image.
-  The following private images cannot be exported:

   -  Full-ECS images
   -  ISO images
   -  Private images created from a Windows, SUSE, Red Hat, Ubuntu, or Oracle Linux public image

-  The image size must be less than 1 TB. Images larger than 128 GB support only fast export.

URI
---

POST /v1/cloudimages/{image_id}/file

:ref:`Table 1 <en-us_topic_0036994315__table23910047154747>` lists the parameters in the URI.

.. _en-us_topic_0036994315__table23910047154747:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                        |
   +=================+=================+=================+====================================================================================================+
   | image_id        | Yes             | String          | Specifies the image ID.                                                                            |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | For details about how to obtain the image ID, see :ref:`Querying Images <en-us_topic_0020091565>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                        |
   +=================+=================+=================+====================================================================================================================+
   | bucket_url      | Yes             | String          | Specifies the URL of the image file in the format of *Bucket name*:*File name*.                                    |
   |                 |                 |                 |                                                                                                                    |
   |                 |                 |                 | .. note::                                                                                                          |
   |                 |                 |                 |                                                                                                                    |
   |                 |                 |                 |    The storage class of the OBS bucket must be **Standard**.                                                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | file_format     | Yes             | String          | Specifies the file format. The value can be **qcow2**, **vhd**, **zvhd**, or **vmdk**.                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | is_quick_export | No              | Boolean         | Whether to enable fast export. The value can be **true** or **false**.                                             |
   |                 |                 |                 |                                                                                                                    |
   |                 |                 |                 | .. note::                                                                                                          |
   |                 |                 |                 |                                                                                                                    |
   |                 |                 |                 |    If fast export is enabled, **file_format** cannot be specified. The exported image file is in the ZVHD2 format. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{Endpoint}/v1/cloudimages/d164b5df-1bc3-4c3f-893e-3e471fd16e64/file
   {
      "bucket_url": "ims-image:centos7_5.qcow2",
      "file_format": "qcow2",
      "is_quick_export": false
   }

Response
--------

-  Response parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                  |
   +=======================+=======================+==============================================================================================+
   | job_id                | String                | Specifies the asynchronous job ID.                                                           |
   |                       |                       |                                                                                              |
   |                       |                       | For details, see :ref:`Querying the Status of an Asynchronous Job <en-us_topic_0022473688>`. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "job_id": "edc89b490d7d4392898e19b2deb34797"
      }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | Returned Value            | Description                                                                                                |
   +===========================+============================================================================================================+
   | 400 Bad Request           | Request error. For details about the returned error code, see :ref:`Error Codes <en-us_topic_0022473689>`. |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                                                                                     |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | 403 Forbidden             | You do not have the rights to perform the operation.                                                       |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                                                                      |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                                                                                    |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                                                                                |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
