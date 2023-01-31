:original_name: en-us_topic_0133188204.html

.. _en-us_topic_0133188204:

Importing an Image File Quickly
===============================

Function
--------

This API is used to quickly create a private image from an oversized external image file that has uploaded to the OBS bucket. Currently, only ZVHD2 and RAW image files are supported, and the size of an image file cannot exceed 1 TB.

The fast image creation function is only available for image files in RAW or ZVHD2 format. For other formats of image files that are smaller than 128 GB, you are advised to import these files with the common method.

The API is an asynchronous one. If it is successfully called, the cloud service system receives the request. However, you need to use the asynchronous job query API to query the image creation status. For details, see :ref:`Asynchronous Job Query <en-us_topic_0022473688>`.

Constraints
-----------

Before importing image files, ensure that the file format is RAW or ZVHD2 and the following have been done:

-  RAW image files have been optimized, and bitmap files have been generated.
-  ZVHD2 image files have been optimized as required.

.. note::

   For how to convert image file formats and generate a bitmap file, see section "Quickly Importing an Image File" in the *Image Management Service User Guide*.

URI
---

POST /v2/cloudimages/quickimport/action

Request
-------

-  Parameters in the request body when an image file is used to create a system disk image

   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type             | Description                                                                                                                                                                                  |
   +=======================+=================+==================+==============================================================================================================================================================================================+
   | name                  | Yes             | String           | Specifies the image name.                                                                                                                                                                    |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562>`.                                                                                                              |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String           | Provides supplementary information about the image.                                                                                                                                          |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562>`.                                                                                                              |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | The value contains a maximum of 1024 characters and consists of only letters and digits. Carriage returns and angle brackets (< >) are not allowed. This parameter is left blank by default. |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os_version            | Yes             | String           | Specifies the OS version.                                                                                                                                                                    |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | This parameter is valid if an external image file uploaded to the OBS bucket is used to create an image. For its value, see :ref:`Values of Related Parameters <en-us_topic_0031617666>`.    |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_url             | Yes             | String           | Specifies the URL of the external image file in the OBS bucket.                                                                                                                              |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | This parameter is mandatory if an external image file in the OBS bucket is used to create an image. The format is *OBS bucket name*:*Image file name*.                                       |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | .. note::                                                                                                                                                                                    |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  |    The storage class of the OBS bucket must be **Standard**.                                                                                                                                 |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_disk              | Yes             | Integer          | Specifies the minimum size (GB) of the system disk.                                                                                                                                          |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | -  This parameter is mandatory if an external image file in the OBS bucket is used to create an image.                                                                                       |
   |                       |                 |                  | -  The value ranges from 1 to 1024 and must be greater than the size of the selected image file.                                                                                             |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No              | Array of strings | Lists the image tags. This parameter is left blank by default.                                                                                                                               |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | Set either **tags** or **image_tags**.                                                                                                                                                       |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_tags            | No              | Array of objects | Lists the image tags. The value is left blank by default.                                                                                                                                    |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | Set either **tags** or **image_tags**.                                                                                                                                                       |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | No              | String           | Specifies the image type. The parameter value is ECS/BMS for system disk images. The default value is **ECS**.                                                                               |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String           | Specifies the enterprise project to which the image belongs.                                                                                                                                 |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | -  If the value is **0** or left blank, the image belongs to the default enterprise project.                                                                                                 |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | -  If the value is a UUID, the image belongs to the enterprise project corresponding to the UUID.                                                                                            |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  |    For more information about enterprise projects and how to obtain enterprise project IDs, see *Enterprise Management User Guide*.                                                          |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | architecture          | No              | String           | Specifies the image architecture type. Available values include:                                                                                                                             |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | -  x86                                                                                                                                                                                       |
   |                       |                 |                  | -  arm                                                                                                                                                                                       |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | The default value is **x86**.                                                                                                                                                                |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  | .. note::                                                                                                                                                                                    |
   |                       |                 |                  |                                                                                                                                                                                              |
   |                       |                 |                  |    If the image architecture is ARM, the boot mode is automatically changed to UEFI.                                                                                                         |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameters description when an image file uploaded to the OBS bucket is used to create an image

   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type             | Description                                                                                                                                                                                                                                                                                                                      |
   +=======================+=================+==================+==================================================================================================================================================================================================================================================================================================================================+
   | name                  | Yes             | String           | Specifies the image name. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562>`.                                                                                                                                                                                                                        |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String           | Provides supplementary information about the image. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562>`. The value contains a maximum of 1024 characters and consists of only letters and digits. Carriage returns and angle brackets (< >) are not allowed. This parameter is left blank by default. |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os_type               | No              | String           | Specifies the OS version.                                                                                                                                                                                                                                                                                                        |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  | When a data disk image created, the value can be **Linux** or **Windows**. The default is **Linux**.                                                                                                                                                                                                                             |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_url             | Yes             | String           | Specifies the URL of the external image file in the OBS bucket.                                                                                                                                                                                                                                                                  |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  | This parameter is mandatory if an external image file in the OBS bucket is used to create an image. The format is *OBS bucket name*:*Image file name*.                                                                                                                                                                           |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  | .. note::                                                                                                                                                                                                                                                                                                                        |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  |    The storage class of the OBS bucket must be **Standard**.                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_disk              | Yes             | Integer          | Specifies the minimum size of the system disk in the unit of GB.                                                                                                                                                                                                                                                                 |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  | This parameter is mandatory if an external image file in the OBS bucket is used to create an image. The value ranges from 1 to 1024.                                                                                                                                                                                             |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No              | Array of strings | Lists the image tags. This parameter is left blank by default.                                                                                                                                                                                                                                                                   |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  | Set either **tags** or **image_tags**.                                                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_tags            | No              | Array of objects | Lists the image tags. The value is left blank by default.                                                                                                                                                                                                                                                                        |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  | Set either **tags** or **image_tags**.                                                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | Yes             | String           | Specifies the image type. The parameter value is DataImage for data disk images.                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String           | Specifies the enterprise project to which the image belongs.                                                                                                                                                                                                                                                                     |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  | -  If the value is **0** or left blank, the image belongs to the default enterprise project.                                                                                                                                                                                                                                     |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  | -  If the value is a UUID, the image belongs to the enterprise project corresponding to the UUID.                                                                                                                                                                                                                                |
   |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                  |    For more information about enterprise projects and how to obtain enterprise project IDs, see *Enterprise Management User Guide*.                                                                                                                                                                                              |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example requests

   -  Creating a system disk image using an external image file

      .. code-block:: text

         POST https://{Endpoint}/v2/cloudimages/quickimport/action

      If parameter **tags** is used:

      ::

         {
             "name": "ims_test_file",
            "description": "Create an image using a file in the OBS bucket.",
             "image_url": "ims-image:centos70.zvhd2",
             "os_version": "CentOS 7.0 64bit",
             "min_disk": 40,
             "type": "ECS",
             "tags":
                 [
                     "aaa.111",
                     "bbb.333",
                     "ccc.444"
                 ]
         }

      If parameter **image_tags** is used:

      ::

         {
             "name": "ims_test_file",
            "description": "Create an image using a file in the OBS bucket.",
             "image_url": "ims-image:centos70.zvhd2",
             "os_version": "CentOS 7.0 64bit",
             "min_disk": 40,
             "type": "ECS",
             "image_tags": [{"key":"key2","value":"value2"},{"key":"key1","value":"value1"}]
         }

   -  Creating a data disk image using an external image file

      .. code-block:: text

         POST https://{Endpoint}/v2/cloudimages/quickimport/action

      If parameter **tags** is used:

      ::

         {
             "name": "ims_test_file",
            "description": "Create an image using a file in the OBS bucket.",
             "image_url": "ims-image:centos70.qcow2",
             "os_type": "Linux",
             "min_disk": 40,
             "type": "DataImage",
             "tags": [
                 "aaa.111",
                 "bbb.333",
                 "ccc.444"
             ]
         }

      If parameter **image_tags** is used:

      ::

         {
             "name": "ims_test_file",
            "description": "Create an image using a file in the OBS bucket.",
             "image_url": "ims-image:centos70.qcow2",
             "os_type": "Linux",
             "min_disk": 40,
             "type": "DataImage",
             "image_tags": [{"key":"key2","value":"value2"},{"key":"key1","value":"value1"}]
         }

Response
--------

-  Response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | job_id                | String                | Specifies the asynchronous job ID.                                       |
   |                       |                       |                                                                          |
   |                       |                       | For details, see :ref:`Asynchronous Job Query <en-us_topic_0022473688>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
           "job_id": "8a12fc664fb4daa3014fb4e581380005"
      }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   +---------------------------+------------------------------------------------------------------------------------------------------------+
   | Return Value              | Description                                                                                                |
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
