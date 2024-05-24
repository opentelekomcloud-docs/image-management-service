:original_name: en-us_topic_0037352185.html

.. _en-us_topic_0037352185:

Checking Whether a Private Image Needs to be Optimized
======================================================

-  If the virtualization type is KVM and VirtIO drivers are not installed, optimization is required.
-  If the virtualization type is KVM and VirtIO drivers are installed, optimization is not required.

Procedure
---------

#. Check whether VirtIO drivers have been installed.

   -  CentOS/EulerOS

      For initramfs, run the following command:

      **lsinitrd** **/boot/initramfs-`uname** **-r`.img** **\|** **grep** **virtio**

      For initrd, run the following command:

      **lsinitrd** **/boot/initrd-`uname** **-r\`** **\|** **grep** **virtio**

   -  Ubuntu/Debian

      **lsinitramfs** **/boot/initrd.img-`uname** **-r\`** **\|grep** **virtio**

   -  SUSE/openSUSE

      -  SUSE 12 SP1/openSUSE 13 or earlier:

         **lsinitrd** **/boot/initrd-`uname -r\` \| grep virtio**

      -  SUSE 12 SP1 or later than SUSE 12 SP1/openSUSE 13:

         For initramfs, run the following command:

         **lsinitrd /boot/initramfs-`uname -r`.img \| grep virtio**

         For initrd, run the following command:

         **lsinitrd /boot/initrd-`uname -r\` \| grep virtio**

   If **virtio** is displayed, VirtIO drivers have been installed. For more information, see :ref:`Creating a Linux System Disk Image from an External Image File <en-us_topic_0030713190>`.

   |image1|

   Otherwise, VirtIO drivers have not been installed. Optimize the private image as instructed in :ref:`Process <en-us_topic_0047501133__section862461118288>`.

.. |image1| image:: /_static/images/en-us_image_0000001443291393.png
