:original_name: en-us_topic_0000001411239213.html

.. _en-us_topic_0000001411239213:

Creating a Full-ECS Image
=========================

Function
--------

This API is used to create a full-ECS image from an ECS, Cloud Server Backup Service (CSBS) backup, or Cloud Backup and Recovery (CBR) backup. The API is an asynchronous one. If it is successfully called, the cloud system receives the request to create a full-ECS image. However, you need to use the asynchronous job query API to query the image creation status. For details, see :ref:`Asynchronous Job Query <en-us_topic_0000001361199224>`.

Constraints (Creating a Full-ECS Image Using an ECS)
----------------------------------------------------

-  When creating a full-ECS image from an ECS, ensure that the ECS has been properly configured, or the image creation may fail.

-  A Windows ECS used to create a full-ECS image cannot have a spanned volume, or data may be lost when ECSs are created from that image.

-  A Linux ECS used to create a full-ECS image cannot have a disk group or logical disk that contains multiple physical disks, or data may be lost when ECSs are created from that image.

-  A full-ECS image cannot be exported or replicated.

-  When creating a full-ECS image from a Windows ECS, you need to change the SAN policy of the ECS to OnlineAll. Otherwise, EVS disks attached to the ECSs created from the image may be offline.

   Windows has three types of SAN policies: **OnlineAll**, **OfflineShared**, and **OfflineInternal**.

   .. table:: **Table 1** SAN policies in Windows

      +-----------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Type            | Description                                                                                                                        |
      +=================+====================================================================================================================================+
      | OnlineAll       | All newly detected disks are automatically brought online.                                                                         |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------+
      | OfflineShared   | All disks on sharable buses, such as iSCSI and FC, are left offline by default, while disks on non-sharable buses are kept online. |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------+
      | OfflineInternal | All newly detected disks are left offline.                                                                                         |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------+

   #. Execute **cmd.exe** and run the following command to query the current SAN policy of the ECS:

      **diskpart**

   #. Run the following command to view the SAN policy of the ECS:

      **san**

      -  If the SAN policy is **OnlineAll**, run the **exit** command to exit DiskPart.

      -  If the SAN policy is not **OnlineAll**, go to :ref:`3 <en-us_topic_0000001411239213__en-us_topic_0116125142_en-us_topic_0089178278_li15110228143312>`.

   #. .. _en-us_topic_0000001411239213__en-us_topic_0116125142_en-us_topic_0089178278_li15110228143312:

      Run the following command to change the SAN policy of the ECS to **OnlineAll**:

      **san policy=onlineall**

Constraints (Creating a Full-ECS Image Using a CSBS Backup)
-----------------------------------------------------------

-  When creating a full-ECS image from a CSBS backup, ensure that the source ECS of the CSBS backup has been properly configured, or the image creation may fail.
-  A CSBS backup used to create a full-ECS image cannot have shared disks.
-  Only an available CSBS backup can be used to create a full-ECS image. A CSBS backup can be used to create only one full-ECS image.
-  A full-ECS image cannot be exported or replicated.

Constraints (Creating a Full-ECS Image Using a CBR Backup)
----------------------------------------------------------

-  When creating a full-ECS image from a CBR backup, ensure that the source ECS of the CBR backup has been properly configured, or the image creation may fail.
-  A CBR backup can be used to create only one full-ECS image.
-  A full-ECS image created from a CBR backup can be shared with other tenants. However, if it is a shared CBR backup, the full-ECS image created from it cannot be shared.
-  A full-ECS image cannot be exported or replicated.

URI
---

POST /v1/cloudimages/wholeimages/action

Request
-------

-  Parameters for creating a full-ECS image using an ECS

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                            |
   +=================+=================+==================+========================================================================================================================================================================================================================================+
   | name            | Yes             | String           | Specifies the image name. For detailed description, see :ref:`Image Attributes <en-us_topic_0000001361199252__section61598810155254>`.                                                                                                 |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String           | Provides supplementary information about the image. For detailed description, see :ref:`Image Attributes <en-us_topic_0000001361199252__section61598810155254>`.                                                                       |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | Array of strings | Lists the image tags. The value is left blank by default.                                                                                                                                                                              |
   |                 |                 |                  |                                                                                                                                                                                                                                        |
   |                 |                 |                  | Use either **tags** or **image_tags**.                                                                                                                                                                                                 |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_tags      | No              | Array of objects | Lists the image tags. The value is left blank by default.                                                                                                                                                                              |
   |                 |                 |                  |                                                                                                                                                                                                                                        |
   |                 |                 |                  | Use either **tags** or **image_tags**.                                                                                                                                                                                                 |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id     | Yes             | String           | Specifies the ECS ID. This parameter is required when an ECS is used to create a full-ECS image.                                                                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                                                                        |
   |                 |                 |                  | To obtain the ECS ID, perform the following operations:                                                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                                        |
   |                 |                 |                  | #. Log in to management console.                                                                                                                                                                                                       |
   |                 |                 |                  | #. Under **Computing**, click **Elastic Cloud Server**.                                                                                                                                                                                |
   |                 |                 |                  | #. In the ECS list, click the name of the ECS and view its ID.                                                                                                                                                                         |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_ram         | No              | Integer          | Specifies the maximum memory of the image in the unit of MB. This parameter is not configured by default.                                                                                                                              |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_ram         | No              | Integer          | Specifies the minimum memory of the image in the unit of MB. The default value is **0**.                                                                                                                                               |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vault_id        | No              | String           | Specifies the ID of the vault to which an ECS is to be added or has been added.                                                                                                                                                        |
   |                 |                 |                  |                                                                                                                                                                                                                                        |
   |                 |                 |                  | To create a full-ECS image from an ECS, create a backup from the ECS and then use the backup to create a full-ECS image. If a CBR backup is created, **vault_id** is mandatory. If a CSBS backup is created, **vault_id** is optional. |
   |                 |                 |                  |                                                                                                                                                                                                                                        |
   |                 |                 |                  | You can obtain the vault ID from the CBR console or section "Querying the Vault List" in *Cloud Backup and Recovery API Reference*.                                                                                                    |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameters in the request body when a CSBS backup or CBR backup is used to create a full-ECS image

   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type             | Description                                                                                                                                                      |
   +==================+=================+==================+==================================================================================================================================================================+
   | name             | Yes             | String           | Specifies the image name. For detailed description, see :ref:`Image Attributes <en-us_topic_0000001361199252__section61598810155254>`.                           |
   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description      | No              | String           | Provides supplementary information about the image. For detailed description, see :ref:`Image Attributes <en-us_topic_0000001361199252__section61598810155254>`. |
   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags             | No              | Array of strings | Lists the image tags. The value is left blank by default.                                                                                                        |
   |                  |                 |                  |                                                                                                                                                                  |
   |                  |                 |                  | Use either **tags** or **image_tags**.                                                                                                                           |
   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_tags       | No              | Array of objects | Lists the image tags. The value is left blank by default.                                                                                                        |
   |                  |                 |                  |                                                                                                                                                                  |
   |                  |                 |                  | Use either **tags** or **image_tags**.                                                                                                                           |
   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_id        | Yes             | String           | Specifies the CSBS backup ID or CBR backup ID.                                                                                                                   |
   |                  |                 |                  |                                                                                                                                                                  |
   |                  |                 |                  | To obtain the CSBS backup ID, perform the following operations:                                                                                                  |
   |                  |                 |                  |                                                                                                                                                                  |
   |                  |                 |                  | #. Log in to the management console.                                                                                                                             |
   |                  |                 |                  | #. Under **Storage**, click **Cloud Server Backup Service**.                                                                                                     |
   |                  |                 |                  | #. In the backup list, expand details of the backup to obtain its ID.                                                                                            |
   |                  |                 |                  |                                                                                                                                                                  |
   |                  |                 |                  | To obtain the CBR backup ID, perform the following operations:                                                                                                   |
   |                  |                 |                  |                                                                                                                                                                  |
   |                  |                 |                  | #. Log in to the management console.                                                                                                                             |
   |                  |                 |                  | #. Under **Storage**, click **Cloud Backup and Recovery**.                                                                                                       |
   |                  |                 |                  | #. On the displayed **Cloud Server Backup** page, click the **Backups** tab and obtain the backup ID from the backup list.                                       |
   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_ram          | No              | Integer          | Specifies the maximum memory of the image in the unit of MB. This parameter is not configured by default.                                                        |
   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_ram          | No              | Integer          | Specifies the minimum memory of the image in the unit of MB. The default value is **0**, indicating that the memory is not restricted.                           |
   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | whole_image_type | No              | String           | Specifies the method of creating a full-ECS image.                                                                                                               |
   |                  |                 |                  |                                                                                                                                                                  |
   |                  |                 |                  | -  If the value is CBR, a CBR backup is used to create a full-ECS image. In this case, backup_id is the CBR backup ID.                                           |
   |                  |                 |                  | -  If the value is CSBS, a CSBS backup is used to create a full-ECS image. In this case, backup_id is the CSBS backup ID.                                        |
   |                  |                 |                  | -  If you do not specify this parameter, value CSBS is used by default.                                                                                          |
   +------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example requests

   -  Creating a full-ECS image from an ECS

      .. code-block:: text

         POST https://{Endpoint}/v1/cloudimages/wholeimages/action

      If parameter **tags** is used:

      ::

         {
                "name": "instance_whole_image",
                "description": "creating an image from an ECS",
                "instance_id": "877a2cda-ba63-4e1e-b95f-e67e48b6129a",
                "vault_id": "de9fcf45-11b2-432c-8562-5c5428574600",
                "tags": [
                    "aaa.111",
                    "bbb.333",
                    "ccc.444"
                ]
         }

      If parameter **image_tags** is used:

      ::

         {
                "name": "instance_whole_image",
                "description": "creating an image from an ECS",
                "instance_id": "877a2cda-ba63-4e1e-b95f-e67e48b6129a",
                "vault_id": "de9fcf45-11b2-432c-8562-5c5428574600",
                "image_tags": [{"key":"key2","value":"value2"},{"key":"key1","value":"value1"}]
         }

   -  Creating a full-ECS image from a CSBS backup or CBR backup

      .. code-block:: text

         POST https://{Endpoint}/v1/cloudimages/wholeimages/action

      If parameter **tags** is used:

      ::

         {
              "name": "backup_whole_image",
              "description": "Creating a full-ECS image from a CBR backup",
              "backup_id": "9b27efab-4a17-4c06-bfa2-3e0cf021d3c3",
              "whole_image_type": "CBR",
              "tags": [
                    "aaa.111",
                    "bbb.333",
                    "ccc.444"
               ]
         }

      If parameter **image_tags** is used:

      ::

         {
              "name": "backup_whole_image",
              "description": "Creating a full-ECS image from a CBR backup",
              "backup_id": "9b27efab-4a17-4c06-bfa2-3e0cf021d3c3",
              "whole_image_type": "CBR",
              "image_tags": [{"key":"key2","value":"value2"},{"key":"key1","value":"value1"}]
         }

Response
--------

-  Response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                    |
   +=======================+=======================+================================================================================+
   | job_id                | String                | Specifies the asynchronous job ID.                                             |
   |                       |                       |                                                                                |
   |                       |                       | For details, see :ref:`Asynchronous Job Query <en-us_topic_0000001361199224>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------+

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

   +---------------------------+------------------------------------------------------------------------------------------------------------------+
   | Returned Value            | Description                                                                                                      |
   +===========================+==================================================================================================================+
   | 400 Bad Request           | Request error. For details about the returned error code, see :ref:`Error Codes <en-us_topic_0000001411239233>`. |
   +---------------------------+------------------------------------------------------------------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                                                                                           |
   +---------------------------+------------------------------------------------------------------------------------------------------------------+
   | 403 Forbidden             | You do not have the rights to perform the operation.                                                             |
   +---------------------------+------------------------------------------------------------------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                                                                            |
   +---------------------------+------------------------------------------------------------------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                                                                                          |
   +---------------------------+------------------------------------------------------------------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                                                                                      |
   +---------------------------+------------------------------------------------------------------------------------------------------------------+
