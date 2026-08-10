:original_name: en-us_topic_0165822629.html

.. _en-us_topic_0165822629:

Querying Supported Image OSs
============================

Function
--------

This API is used to query compatible ECS OSs in the current region.

URI
---

GET /v1/cloudimages/os_version

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                       |
   +=================+=================+=================+===================================================================================================+
   | tag             | No              | String          | **Definition**                                                                                    |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | OS tag. You can query OSs with specified features based on the tag value.                         |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | **Constraints**                                                                                   |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | If this parameter is not specified, all the supported OSs in the current region will be returned. |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | **Range**                                                                                         |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | -  **bms_otc**: indicates the BMS OS versions supported on Open Telekom Cloud.                    |
   |                 |                 |                 | -  **uefi**: indicates the OS versions that support the UEFI boot mode.                           |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | **Default Value**                                                                                 |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | N/A                                                                                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

Example Request
---------------

-  Querying supported OSs

   .. code-block:: text

      GET https://{Endpoint}/v1/cloudimages/os_version

-  Querying supported OSs by filters

   .. code-block:: text

      GET https://{Endpoint}/v1/cloudimages/os_version?tag=uefi

Response
--------

-  Response parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                           |
   +=======================+=======================+=======================================================================================================+
   | *[Array]*             | Array of objects      | **Definition**                                                                                        |
   |                       |                       |                                                                                                       |
   |                       |                       | OSs supported by images. For details, see :ref:`Table 2 <en-us_topic_0165822629__table139163294618>`. |
   |                       |                       |                                                                                                       |
   |                       |                       | **Range**                                                                                             |
   |                       |                       |                                                                                                       |
   |                       |                       | N/A                                                                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0165822629__table139163294618:

   .. table:: **Table 2** Data structure description of the *[Array]* field

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                |
      +=======================+=======================+============================================================================================+
      | platform              | String                | **Definition**                                                                             |
      |                       |                       |                                                                                            |
      |                       |                       | OS platform.                                                                               |
      |                       |                       |                                                                                            |
      |                       |                       | **Range**                                                                                  |
      |                       |                       |                                                                                            |
      |                       |                       | N/A                                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+
      | version_list          | Array of objects      | **Definition**                                                                             |
      |                       |                       |                                                                                            |
      |                       |                       | OS details. For details, see :ref:`Table 3 <en-us_topic_0165822629__table97141914183119>`. |
      |                       |                       |                                                                                            |
      |                       |                       | **Range**                                                                                  |
      |                       |                       |                                                                                            |
      |                       |                       | N/A                                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+

   .. _en-us_topic_0165822629__table97141914183119:

   .. table:: **Table 3** Data structure description of the *[Array]*.version_list field

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                           |
      +=======================+=======================+=======================================================================================================================+
      | platform              | String                | **Definition**                                                                                                        |
      |                       |                       |                                                                                                                       |
      |                       |                       | OS platform.                                                                                                          |
      |                       |                       |                                                                                                                       |
      |                       |                       | **Range**                                                                                                             |
      |                       |                       |                                                                                                                       |
      |                       |                       | N/A                                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | os_version_key        | String                | **Definition**                                                                                                        |
      |                       |                       |                                                                                                                       |
      |                       |                       | OS key value. **os_version** indicates the complete OS version. The default key value is the value of **os_version**. |
      |                       |                       |                                                                                                                       |
      |                       |                       | **Range**                                                                                                             |
      |                       |                       |                                                                                                                       |
      |                       |                       | N/A                                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | os_version            | String                | **Definition**                                                                                                        |
      |                       |                       |                                                                                                                       |
      |                       |                       | Complete OS version.                                                                                                  |
      |                       |                       |                                                                                                                       |
      |                       |                       | **Range**                                                                                                             |
      |                       |                       |                                                                                                                       |
      |                       |                       | N/A                                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | os_bit                | Integer               | **Definition**                                                                                                        |
      |                       |                       |                                                                                                                       |
      |                       |                       | OS bitness.                                                                                                           |
      |                       |                       |                                                                                                                       |
      |                       |                       | **Range**                                                                                                             |
      |                       |                       |                                                                                                                       |
      |                       |                       | The value is **32** or **64**.                                                                                        |
      |                       |                       |                                                                                                                       |
      |                       |                       | -  **32**: 32-bit OS                                                                                                  |
      |                       |                       | -  **64**: 64-bit OS                                                                                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | os_type               | String                | **Definition**                                                                                                        |
      |                       |                       |                                                                                                                       |
      |                       |                       | OS type.                                                                                                              |
      |                       |                       |                                                                                                                       |
      |                       |                       | **Range**                                                                                                             |
      |                       |                       |                                                                                                                       |
      |                       |                       | -  Linux                                                                                                              |
      |                       |                       | -  Windows                                                                                                            |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      [
          {
              "platform": "SUSE",
              "version_list": [
                  {
                      "platform": "SUSE",
                      "os_version_key": "SUSE Linux Enterprise Server 15 64bit",
                      "os_version": "SUSE Linux Enterprise Server 15 64bit",
                      "os_bit": 64,
                      "os_type": "Linux"
                  },
                  {
                      "platform": "SUSE",
                      "os_version_key": "SUSE Linux Enterprise Server 12 SP3 64bit",
                      "os_version": "SUSE Linux Enterprise Server 12 SP3 64bit",
                      "os_bit": 64,
                      "os_type": "Linux"
                  }
              ]
          },
          {
              "platform": "Other",
              "version_list": [
                  {
                      "platform": "Other",
                      "os_version_key": "Other(32 bit)",
                      "os_version": "Other(32 bit)",
                      "os_bit": 32,
                      "os_type": "Linux"
                  }
              ]
          }
      ]

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
