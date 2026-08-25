:original_name: en-us_topic_0036994315.html

.. _en-us_topic_0036994315:

Exporting an Image
==================

Function
--------

This is an extended API used to export a private image to an OBS bucket.

.. note::

   Before exporting an image, ensure that you have Tenant Administrator permissions for OBS.

Constraints
-----------

.. table:: **Table 1** Constraints on exporting images

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                              | Description                                                                                                                                                                                                        |
   +===================================+====================================================================================================================================================================================================================+
   | Region                            | An image can only be exported to a Standard bucket that is in the same region as the image.                                                                                                                        |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image type                        | The following private images cannot be exported:                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                    |
   |                                   | -  Full-ECS images                                                                                                                                                                                                 |
   |                                   | -  ISO images                                                                                                                                                                                                      |
   |                                   | -  Private images created from a Windows, SUSE, Red Hat, Ubuntu, or Oracle Linux public image                                                                                                                      |
   |                                   |                                                                                                                                                                                                                    |
   |                                   | .. note::                                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                    |
   |                                   |    -  Fast export is unavailable for encrypted images. To export an encrypted image, decrypt it first.                                                                                                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image format                      | -  You can export images to the ZVHD2, QCOW2, VMDK, VHD, or ZVHD format. By default, a private image is created in ZVHD2 format. The size of an exported image may vary depending on the export format you select. |
   |                                   | -  Fast export only supports the ZVHD2 format. If you need to export the image in another format, you can use the qemu-img-hw tool to convert the image to the required format after the image is exported.        |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image size                        | The image size must be less than 1 TiB. Images larger than 128 GiB and smaller than 1 TiB only support fast export.                                                                                                |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Time                              | The time required for exporting an image depends on the image size and the number of concurrent export tasks.                                                                                                      |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

URI
---

POST /v1/cloudimages/{image_id}/file

:ref:`Table 2 <en-us_topic_0036994315__table23910047154747>` lists the parameters in the URI.

.. _en-us_topic_0036994315__table23910047154747:

.. table:: **Table 2** Parameter description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                 |
   +=================+=================+=================+=============================================================================================================+
   | image_id        | Yes             | String          | **Definition**                                                                                              |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | Image ID. For details about how to obtain an image ID, see :ref:`Querying Images <en-us_topic_0020091565>`. |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | **Constraints**                                                                                             |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | N/A                                                                                                         |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | **Range**                                                                                                   |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | N/A                                                                                                         |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | **Default Value**                                                                                           |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | N/A                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                    |
   +=================+=================+=================+================================================================================================================================================================================================================+
   | bucket_url      | Yes             | String          | **Definition**                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | URL of the image file in the format of *Bucket name*:*File name*.                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | The storage class of the OBS bucket and the image file must be **Standard**.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Range**                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | N/A                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | N/A                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | file_format     | Yes             | String          | **Definition**                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | File format.                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | N/A                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Range**                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | -  **qcow2**: QCOW2 is a disk image format supported by the QEMU emulator. It is a file that represents a fixed-size block device disk.                                                                        |
   |                 |                 |                 | -  **vhd**: VHD is a virtual disk file format from Microsoft. The VHD file format encapsulates a virtual disk as a single file stored on the host, primarily containing the file system required for ECS boot. |
   |                 |                 |                 | -  **zvhd**: This format uses the ZLIB compression algorithm and supports sequential read and write.                                                                                                           |
   |                 |                 |                 | -  **vmdk**: VMDK is a virtual disk format from VMware. A VMDK file represents a hard disk drive of an ECS, stored within the Virtual Machine File System (VMFS).                                              |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | N/A                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_quick_export | No              | Boolean         | **Definition**                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | Whether to use fast export.                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | If fast export is used, the **file_format** parameter cannot be specified. The exported image file is in the ZVHD2 format.                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Range**                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | The value can be **true** or **false**.                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | -  **true**: Fast export is used.                                                                                                                                                                              |
   |                 |                 |                 | -  **false**: Fast export is not used.                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | false                                                                                                                                                                                                          |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                          |
   +=======================+=======================+======================================================================================================+
   | job_id                | String                | **Definition**                                                                                       |
   |                       |                       |                                                                                                      |
   |                       |                       | Asynchronous job ID.                                                                                 |
   |                       |                       |                                                                                                      |
   |                       |                       | For details, see :ref:`Querying the Progress of an Asynchronous Job <en-us_topic_0000001263414852>`. |
   |                       |                       |                                                                                                      |
   |                       |                       | **Range**                                                                                            |
   |                       |                       |                                                                                                      |
   |                       |                       | N/A                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+

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
   | 403 Forbidden             | Insufficient permissions.                                                                                  |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | 404 Not Found             | Requested resource not found.                                                                              |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                                                                                    |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | 503 Service Unavailable   | Service unavailable.                                                                                       |
   +---------------------------+------------------------------------------------------------------------------------------------------------+
