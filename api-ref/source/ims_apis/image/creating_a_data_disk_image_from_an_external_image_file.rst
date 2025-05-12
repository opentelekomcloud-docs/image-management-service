:original_name: en-us_topic_0083905788.html

.. _en-us_topic_0083905788:

Creating a Data Disk Image from an External Image File
======================================================

Function
--------

This API is used to create a data disk image from a data disk image file uploaded to the OBS bucket. The API is an asynchronous one. If it is successfully called, the cloud service system receives the request. However, you need to use the asynchronous job query API to query the image creation status. For details, see :ref:`Querying the Status of an Asynchronous Job <en-us_topic_0022473688>`.

URI
---

POST /v1/cloudimages/dataimages/action

Request
-------

-  Request parameters

   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                                                                        | Description                                                                                                                                                                                                                                                                               |
   +=======================+=================+=============================================================================+===========================================================================================================================================================================================================================================================================================+
   | name                  | Yes             | String                                                                      | Specifies the image name. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`.                                                                                                                                                          |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String                                                                      | Provides supplementary information about the image.                                                                                                                                                                                                                                       |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`. The value contains a maximum of 1024 characters, including letters and digits. Carriage returns and angle brackets (< >) are not allowed. This parameter is left blank by default. |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os_type               | No              | String                                                                      | Specifies the OS type.                                                                                                                                                                                                                                                                    |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | It can only be Windows or Linux. The default is Linux.                                                                                                                                                                                                                                    |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_url             | Yes             | String                                                                      | Specifies the URL of the external image file in the OBS bucket.                                                                                                                                                                                                                           |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | The format is *OBS bucket name*:*Image file name*.                                                                                                                                                                                                                                        |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | .. note::                                                                                                                                                                                                                                                                                 |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             |    The storage class of the OBS bucket must be **Standard**.                                                                                                                                                                                                                              |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_disk              | Yes             | Integer                                                                     | Specifies the minimum size of the data disk.                                                                                                                                                                                                                                              |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | Value range: 40 GB to 2048 GB                                                                                                                                                                                                                                                             |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cmk_id                | No              | String                                                                      | Specifies a custom key used for encrypting an image. For its value, see the *Key Management Service User Guide*.                                                                                                                                                                          |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No              | Array of strings                                                            | Lists the image tags. This parameter is left blank by default.                                                                                                                                                                                                                            |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | For detailed parameter description, see :ref:`Image Tag Format <en-us_topic_0020092110>`.                                                                                                                                                                                                 |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | Use either **tags** or **image_tags**.                                                                                                                                                                                                                                                    |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_tags            | No              | Array of :ref:`ImageTag <en-us_topic_0083905788__table28981872587>` objects | Lists the image tags. This parameter is left blank by default.                                                                                                                                                                                                                            |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | Use either **tags** or **image_tags**.                                                                                                                                                                                                                                                    |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String                                                                      | Specifies the enterprise project that the image belongs to.                                                                                                                                                                                                                               |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | -  If the value is **0** or left blank, the image belongs to the default enterprise project.                                                                                                                                                                                              |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             | -  If the value is a UUID, the image belongs to the enterprise project corresponding to the UUID.                                                                                                                                                                                         |
   |                       |                 |                                                                             |                                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                             |    For more information about enterprise projects and how to obtain enterprise project IDs, see *Enterprise Management User Guide*.                                                                                                                                                       |
   +-----------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0083905788__table28981872587:

   .. table:: **Table 1** Data structure description of the image_tags field

      ========= ========= ====== ========================
      Parameter Mandatory Type   Description
      ========= ========= ====== ========================
      key       No        string Specifies the tag key.
      value     No        string Specifies the tag value.
      ========= ========= ====== ========================

Example Request
---------------

-  Creating a data disk image with parameter **tags** using a file in an OBS bucket (file address in the bucket: image-test:fedora_data1.qcow2; OS: Linux; minimum size of the data disk: 40 GB)

   .. code-block:: text

      POST https://{Endpoint}/v1/cloudimages/dataimages/action
      {
        "name": "fedora-data1",
        "image_url": "image-test:fedora_data1.qcow2",
        "description":"Data disk 1 of Fedora",
        "min_disk": 40,
        "tags": [
          "aaa.111",
          "bbb.222"
        ],
        "os_type": "Linux"
      }

-  Creating a data disk image with parameter **image_tags** using a file in an OBS bucket (file address in the bucket: image-test:fedora_data1.qcow2; OS: Linux; minimum size of the data disk: 40 GB)

   .. code-block:: text

      POST https://{Endpoint}/v1/cloudimages/dataimages/action
      {
        "name": "fedora-data2",
        "image_url": "image-test:fedora_data1.qcow2",
        "description":"Data disk 2 of Fedora",
        "min_disk": 40,
        "image_tags": [{"key":"aaa","value":"111"},{"key":"bbb","value":"222"}],
        "os_type": "Linux"
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
          "job_id": "4010a32b5f909853015f90aaa24b0015"
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
