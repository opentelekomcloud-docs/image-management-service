:original_name: en-us_topic_0146477763.html

.. _en-us_topic_0146477763:

Overview
========

An ISO file is a disk image of an optical disc. A large number of data files can be compressed into a single ISO file. Likewise, to access the files stored in an ISO, the ISO file needs to be decompressed. For example, you can use a virtual CD-ROM to open an ISO file, or burn the ISO file to a CD or DVD and then use the CD-ROM to read the image.

This section describes how to create a Windows system disk image from an ISO file.

Creation Process
----------------

:ref:`Figure 1 <en-us_topic_0146477763__fig19385204211310>` shows the process of creating a Windows system disk image from an ISO file.

.. _en-us_topic_0146477763__fig19385204211310:

.. figure:: /_static/images/en-us_image_0209970890.png
   :alt: **Figure 1** Creating a Windows system disk image

   **Figure 1** Creating a Windows system disk image

The procedure is as follows:

#. Integrate the VMTools driver into the ISO file

   Windows uses the IDE disk and VirtIO NIC. Before registering an image on the cloud platform, integrate the VMTools driver into the Windows ISO file. For details, see :ref:`Integrating the VMTools Driver into an ISO File <en-us_topic_0146474781>`.

#. Register the ISO file as an ISO image.

   On the management console, register the ISO file that has integrated the VMTools driver as an image. The image is an ISO image and cannot be used to provision ECSs. For details, see :ref:`Registering an ISO File as an ISO Image <en-us_topic_0146474782>`.

#. Create a temporary ECS from the ISO image.

   Use the registered ISO image to create a temporary ECS. The ECS has no OS or driver installed. For details, see :ref:`Creating a Windows ECS from an ISO Image <en-us_topic_0146474783>`.

#. Install an OS and necessary drivers for the temporary ECS and configure related settings.

   The operations include installing an OS and VMTools driver, and configuring NIC attributes. For details, see :ref:`Installing a Windows OS and the VMTools Driver <en-us_topic_0146474784>` and :ref:`1 <en-us_topic_0146480985__li108111309459>` in :ref:`Configuring the ECS and Creating a Windows System Disk Image <en-us_topic_0146480985>`.

#. Create a system disk image from the temporary ECS.

   On the management console, create a system disk image from the temporary ECS on which the installation and configuration have been completed. After the image is created, delete the temporary ECS to prevent it from occupying compute resources. For details, see :ref:`Creating a System Disk Image from a Windows ECS <en-us_topic_0030713149>`.

Constraints
-----------

-  An ISO image created from an ISO file is used only for creating a temporary ECS. It will not be available on the ECS console. You cannot use it to create ECSs or change ECS OSs. You need to install an OS on the temporary ECS and use that ECS to create a system disk image which can be used to create ECSs or change ECS OSs.
-  A temporary ECS has limited functionality. For example, you cannot attach disks to it. You are not advised to use it as a normal ECS.
