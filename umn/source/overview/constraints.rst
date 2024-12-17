:original_name: en-us_topic_0192505040.html

.. _en-us_topic_0192505040:

Constraints
===========

This section describes the constraints on using IMS.

-  :ref:`Creating a private image <en-us_topic_0192505040__table18758121523219>`
-  :ref:`Importing a private image <en-us_topic_0192505040__table172806324219>`
-  :ref:`Sharing images <en-us_topic_0192505040__table15609132017272>`
-  :ref:`Replicating an image <en-us_topic_0192505040__table379519082811>`
-  :ref:`Exporting an image <en-us_topic_0192505040__table56351326285>`
-  :ref:`Encrypting an image <en-us_topic_0192505040__table938085714306>`
-  :ref:`Deleting images <en-us_topic_0192505040__table938085714306>`
-  :ref:`Creating cloud servers from an image <en-us_topic_0192505040__table938085714306>`
-  :ref:`Tagging an image <en-us_topic_0192505040__table938085714306>`

.. _en-us_topic_0192505040__table18758121523219:

.. table:: **Table 1** Constraints on creating a private image

   +------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                                                             | Constraint                                                                                                                                                                                                  |
   +==================================================================+=============================================================================================================================================================================================================+
   | Maximum number of private images that can be created in a region | 50                                                                                                                                                                                                          |
   |                                                                  |                                                                                                                                                                                                             |
   |                                                                  | If you need more, submit a service ticket to increase your quota. For details, see :ref:`Managing Quotas <en-us_topic_0153114116>`.                                                                         |
   +------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Maximum number of concurrent tasks for creating private images   | 40                                                                                                                                                                                                          |
   |                                                                  |                                                                                                                                                                                                             |
   |                                                                  | .. note::                                                                                                                                                                                                   |
   |                                                                  |                                                                                                                                                                                                             |
   |                                                                  |    Currently, only one image can be created in each task.                                                                                                                                                   |
   +------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Creating a system disk image from an ECS                         | -  The ECS must be in the **Stopped** or **Running** state.                                                                                                                                                 |
   +------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Creating a data disk image from an ECS                           | -  The ECS must be in the **Stopped** or **Running** state.                                                                                                                                                 |
   |                                                                  | -  A data disk image can be used to create only one data disk at a time.                                                                                                                                    |
   +------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disk capacity                                                    | -  The system disk capacity of an ECS or a BMS used to create a system disk image must be no greater than 1 TB. If it is greater than 1 TB for an ECS, you can only use the ECS to create a full-ECS image. |
   |                                                                  | -  The data disk capacity of an ECS used to create a data disk image must be no greater than 1 TB. If it is greater than 1 TB, you can only use the ECS to create a full-ECS image.                         |
   +------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Creating a full-ECS image from an ECS or a CSBS or CBR backup    | -  The ECS must be in the **Stopped** or **Running** state.                                                                                                                                                 |
   |                                                                  | -  A CSBS or CBR backup can be used to create only one full-ECS image at a time.                                                                                                                            |
   |                                                                  | -  Only full-ECS images created from CBR backups can be shared. Other full-ECS images cannot be shared.                                                                                                     |
   |                                                                  | -  A full-ECS image cannot be exported or replicated.                                                                                                                                                       |
   +------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0192505040__table172806324219:

.. table:: **Table 2** Constraints on importing a private image

   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                                                      | Constraint                                                                                                                                                                          |
   +===========================================================+=====================================================================================================================================================================================+
   | Importing a system disk image from an external image file | For details about constraints on external image files, see :ref:`Preparing an Image File <en-us_topic_0030713189>` or :ref:`Preparing an Image File <en-us_topic_0030713198>`.      |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Importing a system disk image from an ISO file            | -  Register the ISO file as an ISO image, use the ISO image to create a temporary ECS, install an OS and related drivers on the ECS, and use the ECS to create a system disk image. |
   |                                                           | -  The ISO image cannot be replicated, exported, or encrypted.                                                                                                                      |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Importing a data disk image from an external image file   | The data disk capacity can be 1-2048 GB, and it must also be at least as big as the data disk in the image file.                                                                    |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image format                                              | VMDK, VHD, QCOW2, RAW, VHDX, QED, VDI, QCOW, ZVHD2, and ZVHD                                                                                                                        |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image size                                                | The image size cannot exceed 128 GB.                                                                                                                                                |
   |                                                           |                                                                                                                                                                                     |
   |                                                           | If the image size is between 128 GB and 1 TB, convert the image file into the RAW or ZVHD2 format and import the image through fast import.                                         |
   |                                                           |                                                                                                                                                                                     |
   |                                                           | -  For details about how to convert the image file format, see :ref:`Converting the Image Format Using qemu-img-hw <en-us_topic_0171668652>`.                                       |
   |                                                           | -  For details about fast import, see :ref:`Fast Import of an Image File <en-us_topic_0133773658>`.                                                                                 |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0192505040__table15609132017272:

.. table:: **Table 3** Constrains on sharing images

   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                                                      | Constraint                                                                                                                                                                          |
   +===========================================================+=====================================================================================================================================================================================+
   | Maximum number of tenants an image can be shared with     | System disk image or data disk image: 256                                                                                                                                           |
   |                                                           |                                                                                                                                                                                     |
   |                                                           | Full-ECS image: 10                                                                                                                                                                  |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Maximum number of shared images that a tenant can receive | No limit                                                                                                                                                                            |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Private image status                                      | **Normal**                                                                                                                                                                          |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image sharing                                             | -  Encrypted images cannot be shared.                                                                                                                                               |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Region                                                    | -  There are constraints on the region when cloud servers are created from a shared image. For example, a shared image can be used to create cloud servers only in the same region. |
   +-----------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0192505040__table379519082811:

.. table:: **Table 4** Constraints on replicating an image

   +-----------------------------------------------------------+---------------------------------------------------------------------------------+
   | Item                                                      | Constraint                                                                      |
   +===========================================================+=================================================================================+
   | Maximum size of an image                                  | 128 GB                                                                          |
   +-----------------------------------------------------------+---------------------------------------------------------------------------------+
   | Maximum number of concurrent replication tasks per tenant | 5                                                                               |
   +-----------------------------------------------------------+---------------------------------------------------------------------------------+
   | Private image status                                      | **Normal**                                                                      |
   +-----------------------------------------------------------+---------------------------------------------------------------------------------+
   | Replicating images within a region                        | -  Full-ECS images cannot be replicated.                                        |
   |                                                           | -  Private images created using ISO files do not support in-region replication. |
   +-----------------------------------------------------------+---------------------------------------------------------------------------------+

.. _en-us_topic_0192505040__table56351326285:

.. table:: **Table 5** Constraints on exporting an image

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                              | Constraint                                                                                                                                 |
   +===================================+============================================================================================================================================+
   | Maximum size of an exported image | 1 TB                                                                                                                                       |
   |                                   |                                                                                                                                            |
   |                                   | Images larger than 128 GB only support fast export.                                                                                        |
   |                                   |                                                                                                                                            |
   |                                   | For details about fast export, see :ref:`What Are the Differences Between Import/Export and Fast Import/Export? <en-us_topic_0199451475>`. |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Formats of exported image files   | VMDK, VHD, QCOW2, ZVHD, and ZVHD2                                                                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Private image status              | **Normal**                                                                                                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Exporting an image                | -  Encrypted images cannot be exported through fast export.                                                                                |
   |                                   |                                                                                                                                            |
   |                                   | -  An image can only be exported to a Standard bucket that is in the same region as the image.                                             |
   |                                   | -  The following private images cannot be exported:                                                                                        |
   |                                   |                                                                                                                                            |
   |                                   |    -  Full-ECS images                                                                                                                      |
   |                                   |    -  ISO images                                                                                                                           |
   |                                   |    -  Private images created from a Windows, SUSE, Red Hat, Ubuntu, or Oracle Linux public image                                           |
   |                                   |                                                                                                                                            |
   |                                   | -  The image size must be less than 1 TB. Images larger than 128 GB support only fast export.                                              |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0192505040__table938085714306:

.. table:: **Table 6** Constraints on other image operations

   +--------------------------------------+------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Operation                            | Item                                                                               | Constraint                                                 |
   +======================================+====================================================================================+============================================================+
   | Encrypting an image                  | Creating an encrypted image from an encrypted ECS or an external image file        | -  An encrypted image cannot be shared with others.        |
   |                                      |                                                                                    | -  The key used for encrypting an image cannot be changed. |
   +--------------------------------------+------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Deleting images                      | Private image status                                                               | A published private image cannot be deleted.               |
   +--------------------------------------+------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Creating cloud servers from an image | Number of cloud servers that can be concurrently created using a system disk image | Recommended value: <= 100                                  |
   +--------------------------------------+------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Tagging an image                     | Maximum number of tags that can be added to a private image                        | 10                                                         |
   +--------------------------------------+------------------------------------------------------------------------------------+------------------------------------------------------------+

Other Constraints
-----------------

-  If an ECS is frozen due to overdue payment, it cannot be used to create a private image. You must renew the ECS before using it to create a private image.
-  A private image containing a 32-bit OS cannot be used to create an ECS with larger than 4 GB of memory because the total available address space for a 32-bit OS is 4 GB.
