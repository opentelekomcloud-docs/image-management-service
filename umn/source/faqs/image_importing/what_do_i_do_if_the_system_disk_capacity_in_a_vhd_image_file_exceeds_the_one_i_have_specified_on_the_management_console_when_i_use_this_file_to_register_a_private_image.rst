:original_name: en-us_topic_0058841396.html

.. _en-us_topic_0058841396:

What Do I Do If the System Disk Capacity in a VHD Image File Exceeds the One I Have Specified on the Management Console When I Use This File to Register a Private Image?
=========================================================================================================================================================================

The possible causes may be:

#. You have specified a small value.

   Check the system disk capacity in the VHD image file. Specify a value no less than this value when you use the VHD image file to register an image.

#. After being converted using **qemu-img** or a similar tool, the VHD's virtual disk size becomes smaller than the actual system disk size. For details, see https://bugs.launchpad.net/qemu/+bug/1490611.

   Run the following command to check the VHD image file information:

   .. code-block:: console

      [xxxx@xxxxx test]$ qemu-img info 2g.vhd
      image: 2g.vhd
      file format: vpc
      virtual size: 2.0G (2147991552 bytes)
      disk size: 8.0K
      cluster_size: 2097152

   The virtual size is converted from the actual size (unit: byte) to an integer in GB. After the conversion, the output virtual size **2 GB** is smaller than the input actual size **2.0004 GB** (**2147991552 bytes**). You need to specify an integer larger than the actual size 2.0004 GB on the management console.
