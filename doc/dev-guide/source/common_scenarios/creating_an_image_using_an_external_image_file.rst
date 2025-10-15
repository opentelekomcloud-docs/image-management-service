:original_name: en-us_topic_0109822382.html

.. _en-us_topic_0109822382:

Creating an Image Using an External Image File
==============================================

Scenario
--------

An external image file can also be used to create a private image.

.. note::

   -  The API used here is the same as the one for creating a private image from an ECS except for the parameters in the request body.
   -  The token obtained from Identity and Access Management (IAM) is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to create a data disk image using an external image file

   URI format: POST https://*IMS endpoint*/v1/cloudimages/dataimages/action

Procedure
---------

#. Obtain the token.

#. Send **POST https://**\ *IMS endpoint*\ **/v2/cloudimages/action**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
        "name": "ims_test_file",  //Image name (mandatory, string)
        "description": "Image creation using an image file uploaded to the OBS bucket",  //Image description (optional, string)
        "image_url": "ims-image:centos70.qcow2",  //Image file address (mandatory, string)
        "os_version": "CentOS 7.0 64bit",  //OS version (optional, string)
        "is_config_init":true,  //Initialized or not (optional, boolean)
        "min_disk": 40,  //Minimum system disk size (mandatory, integer)
        "is_config":true,  //Whether to enable automatic configuration (optional, boolean)
        "tags": [
                  "aaa.111",
                  "bbb.333",
                  "ccc.444"
              ]  //Image tag list (optional, array of objects)
      }

   .. note::

      For how to obtain the address of the image file in the OBS bucket, see "Operations on Buckets" in the *Object Storage Service API Reference*.

   -  If the request is successful, a job ID is returned.
   -  If the request fails, an error code and error details are returned. For details, see :ref:`Error Codes <en-us_topic_0110943799>`.

#. Query job details using the job ID by referring to :ref:`Querying Job Details <en-us_topic_0109822371>`.

   If the job status is **SUCCESS**, the private image is successfully created.

   For details about status codes for request errors, see :ref:`Status Codes <en-us_topic_0124290300>`.

#. Obtain the image ID from the job body. You can query for image details based on the image ID. For details, see :ref:`Queries Details About an Image <en-us_topic_0109822404>`.
