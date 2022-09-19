:original_name: en-us_topic_0058841396.html

.. _en-us_topic_0058841396:

What Do I Do If the System Disk Size in a VHD Image File Exceeds the One I Have Specified on the Management Console When I Use This File to Register a Private Image?
=====================================================================================================================================================================

The possible causes may be:

#. You have specified a small value.

   Check the system disk size in the VHD image file. Specify a value no less than this size when you use the VHD image file to register an image.

#. The actual size of the VHD image file is larger than its virtual size, if this VHD image file is generated using **qemu-img** or a similar tool. For details, see https://bugs.launchpad.net/qemu/+bug/1490611.

   Run the following command to check the VHD image file information:

   .. code-block:: console

      [xxxx@xxxxx test]$ qemu-img info 2g.vhd
      image: 2g.vhd
      file format: vpc
      virtual size: 2.0G (2147991552 bytes)
      disk size: 8.0K
      cluster_size: 2097152

   The virtual size is converted from the actual size (unit: byte) to an integer in GB. As a result, the actual file size **2147991552 bytes** (**2.0004 GB**) is larger than the virtual size **2 GB**. Therefore, you need to specify a value larger than the actual size 2.0004 GB. (The system disk size value on the management can only be an integer, so you only need to enter a value larger than **2**.)
