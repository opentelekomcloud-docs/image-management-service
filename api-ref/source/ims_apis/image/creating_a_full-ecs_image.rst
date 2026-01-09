:original_name: en-us_topic_0092380109.html

.. _en-us_topic_0092380109:

Creating a Full-ECS Image
=========================

Function
--------

This API is used to create a full-ECS image from an ECS, Cloud Server Backup Service (CSBS) backup, or Cloud Backup and Recovery (CBR) backup. The API is an asynchronous one. If it is successfully called, the cloud system receives the request to create a full-ECS image. However, you need to use the asynchronous job query API to query the image creation status. For details, see :ref:`Querying the Status of an Asynchronous Job <en-us_topic_0022473688>`.

Constraints (Creating a Full-ECS Image from an ECS)
---------------------------------------------------

-  When creating a full-ECS image from an ECS, ensure that the ECS has been properly configured, or the image creation may fail.
-  A Windows ECS used to create a full-ECS image cannot have a spanned volume, or data may be lost when ECSs are created from that image.
-  A Linux ECS used to create a full-ECS image cannot have a physical disk group or a logical disk that contains multiple physical disks, or data may be lost when ECSs are created from that image.
-  A full-ECS image cannot be exported or replicated.
-  When creating a full-ECS image from a Windows ECS, you need to set the SAN policy of the ECS to **OnlineAll**. Otherwise, EVS disks attached to the ECSs created from the image may be offline. For details, see "Creating a Full-ECS Image from an ECS" > "Setting the ECS SAN Policy to OnlineAll" in *Image Management Service User Guide*.

Constraints (Creating a Full-ECS Image from a CSBS Backup)
----------------------------------------------------------

-  When creating a full-ECS image from a CSBS backup, ensure that the source ECS of the CSBS backup has been properly configured, or the image creation may fail.
-  If an ECS is in **Stopped** state, do not start it when you are using it to create a full-ECS image.
-  A CSBS backup used to create a full-ECS image cannot have shared disks.
-  Only an available CSBS backup can be used to create a full-ECS image. A CSBS backup can be used to create only one full-ECS image.
-  A full-ECS image cannot be exported or replicated.

Constraints (Creating a Full-ECS Image from a CBR Backup)
---------------------------------------------------------

-  When creating a full-ECS image from a CBR backup, ensure that the source ECS of the CBR backup has been properly configured, or the image creation may fail.
-  A CBR backup can be used to create only one full-ECS image.
-  If an ECS is in **Stopped** state, do not start it when you are using it to create a full-ECS image.
-  A full-ECS image created from a CBR backup can be shared with other tenants. However, if it is a shared CBR backup, the full-ECS image created from it cannot be shared.
-  A full-ECS image cannot be exported or replicated.

URI
---

POST /v1/cloudimages/wholeimages/action

Request
-------

-  Parameters for creating a full-ECS image using an ECS

   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type             | Description                                                                                                                                                                                                                            |
   +=======================+=================+==================+========================================================================================================================================================================================================================================+
   | name                  | Yes             | String           | Specifies the image name. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`.                                                                                                       |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String           | Provides supplementary information about the image. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`.                                                                             |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No              | Array of strings | Lists the image tags. This parameter is left blank by default.                                                                                                                                                                         |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | Use either **tags** or **image_tags**.                                                                                                                                                                                                 |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_tags            | No              | Array of objects | Lists the image tags. This parameter is left blank by default.                                                                                                                                                                         |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | Use either **tags** or **image_tags**.                                                                                                                                                                                                 |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | For details about **image_tags**, see :ref:`Table 1 <en-us_topic_0092380109__table1394012426522>`.                                                                                                                                     |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id           | Yes             | String           | Specifies the ECS ID. This parameter is required when an ECS is used to create a full-ECS image.                                                                                                                                       |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | To obtain the ECS ID, perform the following operations:                                                                                                                                                                                |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | #. Log in to the management console.                                                                                                                                                                                                   |
   |                       |                 |                  | #. Under **Computing**, click **Elastic Cloud Server**.                                                                                                                                                                                |
   |                       |                 |                  | #. In the ECS list, click the name of the ECS and view its ID.                                                                                                                                                                         |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String           | Specifies the enterprise project that the image belongs to.                                                                                                                                                                            |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | -  If the value is **0** or left blank, the image belongs to the default enterprise project.                                                                                                                                           |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | -  If the value is a UUID, the image belongs to the enterprise project corresponding to the UUID.                                                                                                                                      |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  |    For more information about enterprise projects and how to obtain enterprise project IDs, see *Enterprise Management User Guide*.                                                                                                    |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_ram               | No              | Integer          | Specifies the maximum memory of the image in the unit of MB. This parameter is not configured by default.                                                                                                                              |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_ram               | No              | Integer          | Specifies the minimum memory of the image in the unit of MB. The default value is **0**.                                                                                                                                               |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vault_id              | No              | String           | Specifies the ID of the vault to which an ECS is to be added or has been added.                                                                                                                                                        |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | To create a full-ECS image from an ECS, create a backup from the ECS and then use the backup to create a full-ECS image. If a CBR backup is created, **vault_id** is mandatory. If a CSBS backup is created, **vault_id** is optional. |
   |                       |                 |                  |                                                                                                                                                                                                                                        |
   |                       |                 |                  | You can obtain the vault ID from the CBR console or section "Querying the Vault List" in *Cloud Backup and Recovery API Reference*.                                                                                                    |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameters in the request body when a CSBS backup or CBR backup is used to create a full-ECS image

   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type             | Description                                                                                                                                                                              |
   +=======================+=================+==================+==========================================================================================================================================================================================+
   | name                  | Yes             | String           | Specifies the image name. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`.                                                         |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String           | Provides supplementary information about the image. For detailed description, see :ref:`Image Attributes <en-us_topic_0020091562__section61598810155254>`.                               |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No              | Array of strings | Lists the image tags. This parameter is left blank by default.                                                                                                                           |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | Use either **tags** or **image_tags**.                                                                                                                                                   |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_tags            | No              | Array of objects | Lists the image tags. This parameter is left blank by default.                                                                                                                           |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | Use either **tags** or **image_tags**.                                                                                                                                                   |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | For details about **image_tags**, see :ref:`Table 1 <en-us_topic_0092380109__table1394012426522>`.                                                                                       |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_id             | Yes             | String           | Specifies the CSBS backup ID or CBR backup ID.                                                                                                                                           |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | To obtain the CSBS backup ID, perform the following operations:                                                                                                                          |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | #. Log in to the management console.                                                                                                                                                     |
   |                       |                 |                  | #. Under **Storage**, click **Cloud Server Backup Service**.                                                                                                                             |
   |                       |                 |                  | #. In the backup list, expand details of the backup to obtain its ID.                                                                                                                    |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | To obtain the CBR backup ID, perform the following operations:                                                                                                                           |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | #. Log in to the management console.                                                                                                                                                     |
   |                       |                 |                  | #. Under **Storage**, click **Cloud Backup and Recovery**.                                                                                                                               |
   |                       |                 |                  | #. On the displayed **Cloud Server Backup** page, click the **Backups** tab and obtain the backup ID from the backup list.                                                               |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String           | Specifies the enterprise project that the image belongs to.                                                                                                                              |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | -  If the value is **0** or left blank, the image belongs to the default enterprise project.                                                                                             |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | -  If the value is a UUID, the image belongs to the enterprise project corresponding to the UUID.                                                                                        |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  |    For more information about enterprise projects and how to obtain enterprise project IDs, see *Enterprise Management User Guide*.                                                      |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_ram               | No              | Integer          | Specifies the maximum memory of the image in the unit of MB. This parameter is not configured by default.                                                                                |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_ram               | No              | Integer          | Specifies the minimum memory of the image in the unit of MB. The default value is **0**, indicating that the memory is not restricted.                                                   |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | whole_image_type      | No              | String           | Specifies the method of creating a full-ECS image.                                                                                                                                       |
   |                       |                 |                  |                                                                                                                                                                                          |
   |                       |                 |                  | -  If a CBR backup is used to create a full-ECS image, this parameter is mandatory and the value must be **CBR**. In this case, **backup_id** is the CBR backup ID.                      |
   |                       |                 |                  | -  If a CSBS backup is used to create a full-ECS image, this parameter can be left blank and the default value **CSBS** will be used. In this case, **backup_id** is the CSBS backup ID. |
   +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0092380109__table1394012426522:

.. table:: **Table 1** Data structure of the image_tags field

   ========= ========= ====== ========================
   Parameter Mandatory Type   Description
   ========= ========= ====== ========================
   key       Yes       String Specifies the tag key.
   value     Yes       String Specifies the tag value.
   ========= ========= ====== ========================

Example Request
---------------

-  Creating a full-ECS image with parameter **tags** using an ECS (ID: 877a2cda-ba63-4e1e-b95f-e67e48b6129a)

   .. code-block:: text

      POST https://{Endpoint}/v1/cloudimages/wholeimages/action
      {
             "name": "instance_whole_image",
             "description": "Create an image from an ECS",
             "instance_id": "877a2cda-ba63-4e1e-b95f-e67e48b6129a",
             "vault_id": "de9fcf45-11b2-432c-8562-5c5428574600",
             "tags": [
                 "aaa.111",
                 "bbb.333",
                 "ccc.444"
             ]
      }

-  Creating a full-ECS image with parameter **image_tags** using an ECS (ID: 877a2cda-ba63-4e1e-b95f-e67e48b6129a)

   .. code-block:: text

      POST https://{Endpoint}/v1/cloudimages/wholeimages/action
      {
             "name": "instance_whole_image",
             "description": "Create an image from an ECS",
             "instance_id": "877a2cda-ba63-4e1e-b95f-e67e48b6129a",
             "vault_id": "de9fcf45-11b2-432c-8562-5c5428574600",
             "image_tags": [{"key":"key2","value":"value2"},{"key":"key1","value":"value1"}]
      }

-  Creating a full-ECS image with parameter **tags** using a CSBS backup or CBR backup (ID: 9b27efab-4a17-4c06-bfa2-3e0cf021d3c3)

   .. code-block:: text

      POST https://{Endpoint}/v1/cloudimages/wholeimages/action
      {
           "name": "backup_whole_image",
           "description": "Create a full-ECS image from a CBR backup",
           "backup_id": "9b27efab-4a17-4c06-bfa2-3e0cf021d3c3",
           "whole_image_type": "CBR",
           "tags": [
                 "aaa.111",
                 "bbb.333",
                 "ccc.444"
            ]
      }

-  Creating a full-ECS image with parameter **image_tags** using a CSBS backup or CBR backup (ID: 9b27efab-4a17-4c06-bfa2-3e0cf021d3c3)

   .. code-block:: text

      POST https://{Endpoint}/v1/cloudimages/wholeimages/action
      {
           "name": "backup_whole_image",
           "description": "Create a full-ECS image from a CBR backup",
           "backup_id": "9b27efab-4a17-4c06-bfa2-3e0cf021d3c3",
           "whole_image_type": "CBR",
           "image_tags": [{"key":"key2","value":"value2"},{"key":"key1","value":"value1"}]
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
