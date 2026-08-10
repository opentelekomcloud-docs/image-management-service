:original_name: en-us_topic_0037131984.html

.. _en-us_topic_0037131984:

Registering an Image
====================

Function
--------

This API is used to register an image file as an uninitialized private image on the cloud platform.

The following describes how to use this API:

#. Upload the image file to an OBS bucket. For details, see "Object Storage Service User Guide".

#. .. _en-us_topic_0037131984__li40093194:

   Use the image metadata creation API to create image metadata. After the API is invoked successfully, save the image ID. For how to create image metadata, see :ref:`Creating Image Metadata (Native OpenStack API) <en-us_topic_0031615565>`.

#. Use the API for registering images and the image ID obtained in :ref:`2 <en-us_topic_0037131984__li40093194>` to register the image file as a private image.

#. After this asynchronous API is successfully called, the backend receives a request. Query the image status using the image ID and check whether the image file is successfully registered. When the image status changes to **active**, the image file is successfully registered as a private image.

   For details about how to query an asynchronous job, see :ref:`Querying the Progress of an Asynchronous Job <en-us_topic_0000001263414852>`.

.. note::

   Before registering an image file, ensure that you have Tenant Administrator permissions for OBS.

URI
---

PUT /v1/cloudimages/{image_id}/upload

:ref:`Table 1 <en-us_topic_0037131984__table23910047154747>` lists the parameters in the URI.

.. _en-us_topic_0037131984__table23910047154747:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================================================================================================+
   | image_id        | Yes             | String          | **Definition**                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | Image ID.                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | -  **image_id** is the ID of the image you created by invoking the API for creating image metadata. Registration may fail if you use other image IDs.                                                                                                                   |
   |                 |                 |                 | -  After this API is invoked, you can check the image status with the image ID. When the image status changes to **active**, the image file is successfully registered. For details, see :ref:`Querying Image Details (Native OpenStack API) <en-us_topic_0020091566>`. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | N/A                                                                                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | N/A                                                                                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | N/A                                                                                                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                             |
   +=================+=================+=================+=========================================================================================================+
   | image_url       | Yes             | String          | **Definition**                                                                                          |
   |                 |                 |                 |                                                                                                         |
   |                 |                 |                 | URL of the image file, in the format of *<bucket>*:*<file>*.                                            |
   |                 |                 |                 |                                                                                                         |
   |                 |                 |                 | **Constraints**                                                                                         |
   |                 |                 |                 |                                                                                                         |
   |                 |                 |                 | The storage class of the OBS bucket and image file must be **Standard**.                                |
   |                 |                 |                 |                                                                                                         |
   |                 |                 |                 | **Range**                                                                                               |
   |                 |                 |                 |                                                                                                         |
   |                 |                 |                 | Image files in the bucket can be in ZVHD, QCOW2, VHD, RAW, VHDX, QED, VDI, QCOW, ZVHD2, or VMDK format. |
   |                 |                 |                 |                                                                                                         |
   |                 |                 |                 | **Default Value**                                                                                       |
   |                 |                 |                 |                                                                                                         |
   |                 |                 |                 | N/A                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------+

Example Request
---------------

Registering an image (URL of the image file: bucketname:Centos6.5-disk1.vmdk)

.. code-block:: text

   PUT https://{Endpoint}/v1/cloudimages/4ca46bf1-5c61-48ff-b4f3-0ad4e5e3ba86/upload
   {
      "image_url": "bucketname:Centos6.5-disk1.vmdk"
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

      HTTP/1.1 200

   ::

      {
         "job_id":" b912fb4a4c464b568ecfca1071b21b10"
      }

Returned Values
---------------

-  Normal

   200

-  Abnormal

+------------------+------------------------------------------------------------------------------------------------------------+
| Returned Value   | Description                                                                                                |
+==================+============================================================================================================+
| 400 Bad Request  | Request error. For details about the returned error code, see :ref:`Error Codes <en-us_topic_0022473689>`. |
+------------------+------------------------------------------------------------------------------------------------------------+
| 401 Unauthorized | Authentication failed.                                                                                     |
+------------------+------------------------------------------------------------------------------------------------------------+
| 403 Forbidden    | Insufficient permissions.                                                                                  |
+------------------+------------------------------------------------------------------------------------------------------------+
| 404 Not Found    | Requested resource not found.                                                                              |
+------------------+------------------------------------------------------------------------------------------------------------+
