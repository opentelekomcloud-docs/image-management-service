:original_name: en-us_topic_0031615566.html

.. _en-us_topic_0031615566:

Uploading an Image (Native OpenStack API)
=========================================

Function
--------

This API is used to upload a local image to the cloud platform. The image to be uploaded must be smaller than 128 GB.

For more information about how to use external files to create images, see sections "Creating a Private Windows Image Using an External Image File" and "Creating a Private Linux Image Using an External Image File" in *Image Management Service User Guide*.

The following describes how to use this API:

#. Prepare the image to be uploaded. The image can be in QCOW2, VMDK, VHD, RAW, VHDX, QED, VDI, QCOW, ZVHD2, or ZVHD format.

#. .. _en-us_topic_0031615566__li57474254155728:

   Create metadata for the image by performing the operations in :ref:`Creating Image Metadata (Native OpenStack API) <en-us_topic_0031615565>`. After the API is invoked successfully, save the image ID.

#. Upload the image file with the image ID obtained in :ref:`2 <en-us_topic_0031615566__li57474254155728>`.

URI
---

PUT /v2/images/{image_id}/file

:ref:`Table 1 <en-us_topic_0031615566__table23910047154747>` lists the parameters in the URI.

.. _en-us_topic_0031615566__table23910047154747:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================+
   | image_id        | Yes             | String          | Specifies the image ID.                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | -  **image_id** is the ID of the image you created by invoking the API for creating image metadata. Image upload may fail if you use other image IDs.            |
   |                 |                 |                 | -  After this API is invoked, you can check the image status with the image ID. When the image status changes to **active**, the image is uploaded successfully. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   -  AK/SK authentication supports API requests with a body not larger than 12 MB. For API requests with a larger body, token authentication is recommended.
   -  API Gateway checks the time format and compares the request time with the time when API Gateway received the request. If the time difference exceeds 15 minutes, API Gateway will reject the request. So, the local time on the client must be synchronized with the clock server to avoid a large offset in the value of **X-Sdk-Date** in the request header.

Request
-------

-  Request parameters

   ============ ========= ==== ========================================
   Parameter    Mandatory Type Description
   ============ ========= ==== ========================================
   *image_file* Yes       file Specifies the local file to be uploaded.
   ============ ========= ==== ========================================

Example Request
---------------

.. code-block:: text

   PUT https://{Endpoint}/v2/images/84ac7f2b-bf19-4efb-86a0-b5be8771b476/file

.. note::

   If you use the curl command to call the API, the example request is as follows:

   .. code-block::

      curl -i --insecure 'https://IP/v2/images/84ac7f2b-bf19-4efb-86a0-b5be8771b476/file' -X PUT -H "X-Auth-Token: $mytoken" -H "Content-Type:application/octet-stream" -T /mnt/userdisk/images/suse.zvhd

Response
--------

-  Response parameters

   None

-  Example response

   .. code-block:: text

      HTTP/1.1 204

Returned Values
---------------

-  Normal

   204

-  Abnormal

   +------------------+------------------------------------------------------------------------------+
   | Returned Value   | Description                                                                  |
   +==================+==============================================================================+
   | 400 Bad Request  | Request error. For details, see :ref:`Error Codes <en-us_topic_0022473689>`. |
   +------------------+------------------------------------------------------------------------------+
   | 401 Unauthorized | Authentication failed.                                                       |
   +------------------+------------------------------------------------------------------------------+
   | 403 Forbidden    | You do not have the rights to perform the operation.                         |
   +------------------+------------------------------------------------------------------------------+
   | 404 Not Found    | The requested resource was not found.                                        |
   +------------------+------------------------------------------------------------------------------+
   | 409 Conflict     | Request conflict.                                                            |
   +------------------+------------------------------------------------------------------------------+
   | 500 System Error | System error.                                                                |
   +------------------+------------------------------------------------------------------------------+
