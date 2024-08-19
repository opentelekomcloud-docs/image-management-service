:original_name: en-us_topic_0058841396.html

.. _en-us_topic_0058841396:

Why Did My VHD Upload Fail? Why Does the System Say the System Disk in the VHD Image File Is Larger Than What I Specified on the Management Console?
====================================================================================================================================================

The possible causes may be:

#. Too small a value was specified when registering the image. Check the system disk capacity in the VHD image file. Specify a value at least this large when you use the VHD image file to register an image.

#. The VHD's actual disk size is larger than its virtual size. This can happen if the VHD image file was generated using **qemu-img** or a similar tool. For details, see https://bugs.launchpad.net/qemu/+bug/1490611.

   Run the following command to check the VHD image file information:

   .. code-block:: console

      [xxxx@xxxxx test]$ qemu-img info 2g.vhd
      image: 2g.vhd
      file format: vpc
      virtual size: 2.0G (2147991552 bytes)
      disk size: 8.0K
      cluster_size: 2097152

   The virtual size is always an integer number of GBs. As a result, if an actual size is, like in the example here, **2147991552 bytes** (**2.0004 GB**), the virtual size will be only **2 GB**. In this example, you need to specify an integer larger than the actual size 2.0004 GB. The system disk capacity on the management console can only be an integer value, so you enter an integer larger than 2 GB.
