:original_name: en-us_topic_0000002183615189.html

.. _en-us_topic_0000002183615189:

Overview
========

Before creating a private image, you need to configure the image source to initialize the private image and improve the image availability.

You can configure them as instructed in the following tables.

-  :ref:`Table 1 <en-us_topic_0000002183615189__table1978918558314>`
-  :ref:`Table 2 <en-us_topic_0000002183615189__table1182513010515>`

Image Source: ECS or Image File
-------------------------------

.. _en-us_topic_0000002183615189__table1978918558314:

.. table:: **Table 1** ECS configurations

   +-----------------------------------+------------------------------------------------------------------------------------------------+
   | OS                                | Configuration                                                                                  |
   +===================================+================================================================================================+
   | Windows                           | -  :ref:`Configuring DHCP <en-us_topic_0030713152>`                                            |
   |                                   | -  :ref:`Enabling Remote Desktop Connection <en-us_topic_0030713155>`                          |
   |                                   | -  :ref:`(Optional) Installing Special Windows Drivers <en-us_topic_0081795392>`               |
   |                                   | -  :ref:`(Optional) Installing and Configuring Cloudbase-Init <en-us_topic_0030730602>`        |
   |                                   | -  Installing Guest OS Drivers (:ref:`VirtIO <en-us_topic_0000001841305273>` Drivers)          |
   |                                   | -  :ref:`Running Sysprep <en-us_topic_0093887081>`                                             |
   +-----------------------------------+------------------------------------------------------------------------------------------------+
   | Linux                             | -  :ref:`Configuring DHCP <en-us_topic_0030713176>`                                            |
   |                                   | -  :ref:`(Optional) Installing Special Linux Drivers <en-us_topic_0082002007>`                 |
   |                                   | -  :ref:`(Optional) Installing and Configuring Cloud-Init <en-us_topic_0030730603>`            |
   |                                   | -  :ref:`Deleting Files from the Network Rule Directory <en-us_topic_0069904570>`              |
   |                                   | -  :ref:`Changing Disk Identifiers in the GRUB File to UUID <en-us_topic_0086020895>`          |
   |                                   | -  :ref:`Changing Disk Identifiers in the fstab File to UUID <en-us_topic_0086024961>`         |
   |                                   | -  :ref:`(Optional) Installing Native KVM Drivers on a KVM ECS <en-us_topic_0000001120952155>` |
   |                                   | -  :ref:`Detaching Data Disks from an ECS <en-us_topic_0030713179>`                            |
   |                                   | -  :ref:`Configuring Console Logging <en-us_topic_0057450886>`                                 |
   +-----------------------------------+------------------------------------------------------------------------------------------------+

.. note::

   -  If the ECS was created from a public image, Cloud-Init has been installed in it by default.

.. _en-us_topic_0000002183615189__table1182513010515:

.. table:: **Table 2** Image file configurations

   +-----------------------------------+------------------------------------------------------------------------------------------------+
   | OS                                | Configuration                                                                                  |
   +===================================+================================================================================================+
   | Windows                           | -  :ref:`Configuring DHCP <en-us_topic_0030713152>`                                            |
   |                                   | -  :ref:`Enabling Remote Desktop Connection <en-us_topic_0030713155>`                          |
   |                                   | -  :ref:`(Optional) Installing and Configuring Cloudbase-Init <en-us_topic_0030730602>`        |
   |                                   | -  Installing Guest OS Drivers (:ref:`VirtIO <en-us_topic_0000001841305273>` Drivers)          |
   |                                   | -  :ref:`(Optional) Enabling NIC Multi-Queue <en-us_topic_0085214115>`                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------+
   | Linux                             | -  :ref:`Configuring DHCP <en-us_topic_0030713176>`                                            |
   |                                   | -  :ref:`Deleting Files from the Network Rule Directory <en-us_topic_0069904570>`              |
   |                                   | -  :ref:`Changing Disk Identifiers in the GRUB File to UUID <en-us_topic_0086020895>`          |
   |                                   | -  :ref:`Changing Disk Identifiers in the fstab File to UUID <en-us_topic_0086024961>`         |
   |                                   | -  :ref:`(Optional) Installing Native KVM Drivers on a KVM ECS <en-us_topic_0000001120952155>` |
   |                                   | -  :ref:`(Optional) Enabling NIC Multi-Queue <en-us_topic_0085214115>`                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------+

.. note::

   -  To use an image file to create a private image, you are advised to perform the preceding operations on the VM from which the image file is exported.
   -  When you register a Windows image file as a private image, if you select **Enable automatic configuration**, the cloud platform will check the image file for Guest OS drivers. If no Guest OS drivers are found, the cloud platform will try to install them automatically.
