:original_name: en-us_topic_0000002183332373.html

.. _en-us_topic_0000002183332373:

Overview
========

A private image contains an OS or service data, preinstalled public applications, and a user's personal applications. Private images are only available to the users who created them.

You can import an image file from your local PC or other cloud platforms to IMS and register it as a private image. Then, you can use the image to create new cloud servers or data disks, or change the OS for existing cloud servers. This way, your services can be migrated to the cloud or in the cloud.

The methods for creating a private image from an image file vary depending on the image file format and size.

.. table:: **Table 1** Overview

   +-------------------------------------------------+------------------------+--------------------------------------------------------------------------------------------------+
   | Image File Format                               | Image File Size        | Helpful Link                                                                                     |
   +=================================================+========================+==================================================================================================+
   | VMDK, VHD, QCOW2, VHDX, QED, VDI, QCOW, or ZVHD | No larger than 128 GiB | -  :ref:`Creating a Windows System Disk Image from an Image File <en-us_topic_0000002214579410>` |
   |                                                 |                        | -  :ref:`Creating a Linux System Disk Image from an Image File <en-us_topic_0030713190>`         |
   |                                                 |                        | -  :ref:`Creating a Data Disk Image from an External Image File <en-us_topic_0084064672>`        |
   +-------------------------------------------------+------------------------+--------------------------------------------------------------------------------------------------+
   | RAW or ZVHD2                                    | No larger than 1 TiB   | -  :ref:`Fast Import of an Image File <en-us_topic_0030713151>`                                  |
   |                                                 |                        | -  :ref:`Creating a Data Disk Image from an External Image File <en-us_topic_0084064672>`        |
   +-------------------------------------------------+------------------------+--------------------------------------------------------------------------------------------------+

You can also create a private image from a cloud server or a backup. For details, see :ref:`Overview <en-us_topic_0013901628>`.
