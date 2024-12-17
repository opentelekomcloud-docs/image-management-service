:original_name: en-us_topic_0032307025.html

.. _en-us_topic_0032307025:

What Will the System Do to an Image File When I Use the File to Register a Private Image?
=========================================================================================

You are advised to enable automatic configuration when registering a private image using an image file. Then, the system will perform the following operations:

Linux
-----

-  Check whether any PV drivers exist. If yes, the system deletes them.
-  Modify the **grub** and **syslinux** configuration files to add OS kernel boot parameters and change disk partition names to UUID.
-  Change disk partition names in the **/etc/fstab** file to UUID.
-  Check whether the initrd file has IDE driver. If no, the system will load the IDE driver.
-  Modify the X Window configuration file **/etc/X11/xorg.conf** to prevent display failures.
-  Delete services of VMware tools.
-  Record the latest automatic modification made to the image into **/var/log/rainbow_modification_record.log**.
-  Copy built-in VirtIO drivers to **initrd** or **initramfs**. For details, see :ref:`External Image File Formats and Supported OSs <en-us_topic_0030713143>`.

.. note::

   For the following image files, the system does not copy built-in VirtIO drivers after **Enable automatic configuration** is selected:

   -  Image files whose **/usr** directory is an independent partition
   -  Fedora 29 64bit, Fedora 30 64bit, and CentOS 8.0 64bit image files that use the XFS file system
   -  SUSE 12 SP4 64bit image files that use the ext4 file system

Windows
-------

-  Restore the IDE driver so that the OS can use this driver for its initial start.
-  Delete the registry keys of the mouse and keyboard and generate the registry keys again to ensure that the mouse and keyboard are available on the new cloud platform.
-  Restore DHCP so that the OS will dynamically obtain information such as the IP address based on the DHCP protocol.
