:original_name: en-us_topic_0030713221.html

.. _en-us_topic_0030713221:

Can I Specify the System Disk Capacity When I Create an ECS Using an Image?
===========================================================================

If you create an ECS from a private system disk image, you can change the instance specifications and system disk type, but the system disk size must be greater than that in the image.

If you create an ECS from a private full-ECS image that contains one or more data disks, the system automatically sets the data disk parameters for the ECS. You can increase the capacity of a system disk or data disks, but cannot decrease it.

Yes, but you cannot create a system disk smaller than the original and the maximum allowed is 30,768 GB.

.. note::

   Ensure that your ECS OS can support the system disk size you specified.
