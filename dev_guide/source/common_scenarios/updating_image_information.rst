:original_name: en-us_topic_0109822367.html

.. _en-us_topic_0109822367:

Updating Image Information
==========================

Scenario
--------

Image attributes can be modified to update image information.

.. note::

   -  Only the name and description of private images can be changed.
   -  The token obtained from Identity and Access Management (IAM) is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to update image information (Native OpenStack API)

   URI format: PATCH https://*IMS endpoint*/v2/images/*Image ID*

Procedure
---------

#. Obtain the token.

#. Send **PATCH https://**\ *IMS endpoint*\ **/v2/cloudimages/**\ *Image ID*.

#. Specify the following parameters in the request body:

   +-----------------+-----------------+-----------------------------------+-----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                              | Description                                                                                         |
   +=================+=================+===================================+=====================================================================================================+
   | op              | Yes             | String                            | Specifies the operation. The value can be **add**, **replace**, or **remove**.                      |
   +-----------------+-----------------+-----------------------------------+-----------------------------------------------------------------------------------------------------+
   | path            | Yes             | String                            | Specifies the name of the attribute to be modified. A slash (/) needs to be added in front of it.   |
   |                 |                 |                                   |                                                                                                     |
   |                 |                 |                                   | You can modify the following attributes:                                                            |
   |                 |                 |                                   |                                                                                                     |
   |                 |                 |                                   | -  **name**: image name                                                                             |
   |                 |                 |                                   | -  **\__description**: image description                                                            |
   |                 |                 |                                   | -  **\__support_xen**: Xen is supported.                                                            |
   |                 |                 |                                   | -  **\__support_largememory**: Ultra-large memory is supported.                                     |
   |                 |                 |                                   | -  **\__support_diskintensive**: Intensive storage is supported.                                    |
   |                 |                 |                                   | -  **\__support_highperformance**: High-performance computing (HPC) is supported.                   |
   |                 |                 |                                   | -  **\__support_xen_gpu_type**: GPU-accelerated ECSs that use Xen for virtualization are supported. |
   |                 |                 |                                   | -  **\__support_xen_hana**: HANA ECSs that use Xen for virtualization are supported.                |
   |                 |                 |                                   | -  **min_ram**: minimum memory                                                                      |
   |                 |                 |                                   | -  **hw_vif_multiqueue_enabled**: The NIC multi-queue feature is supported.                         |
   |                 |                 |                                   | -  **hw_firmware_type**: boot mode. The value can be **bios** or **uefi**.                          |
   |                 |                 |                                   |                                                                                                     |
   |                 |                 |                                   | You can add or delete extended attributes.                                                          |
   +-----------------+-----------------+-----------------------------------+-----------------------------------------------------------------------------------------------------+
   | value           | Yes             | Determined by the attribute value | Specifies the new value of the attribute.                                                           |
   +-----------------+-----------------+-----------------------------------+-----------------------------------------------------------------------------------------------------+

   Example request:

   .. code-block::

      [
          {
              "op": "replace",
              "path": "/name",
              "value": "ims_test"
          }
      ]

#. Refer to "Updating Image Information" in the *Image Management Service API Reference* for details about the request response parameters.

   For details about status codes for request exceptions, see :ref:`Status Codes <en-us_topic_0124290300>`.
