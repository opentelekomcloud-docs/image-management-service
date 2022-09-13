:original_name: en-us_topic_0069904570.html

.. _en-us_topic_0069904570:

Deleting Files from the Network Rule Directory
==============================================

Scenarios
---------

To prevent NIC name drift when you use a private image to create ECSs, you need to delete files from the network rule directory of the VM where the ECS or image file is located during the private image creation.

.. note::

   When registering an external image file as a private image, delete files from the network rule directory on the VM where the external image file is located. You are advised to delete the files on the VM and then export the image file.

Prerequisites
-------------

An OS and VirtIO drivers have been installed on the ECS.

Procedure
---------

#. Run the following command to query files in the network rule directory:

   **ls -l /etc/udev/rules.d**

#. Run the following commands to delete the files whose names contain **persistent** and **net** from the network rule directory:

   Example:

   **rm** **/etc/udev/rules.d/**\ *30-*\ **net_persistent**\ *-names*\ **.rules**

   **rm** **/etc/udev/rules.d/**\ *70-*\ **persistent-net.rules**

   The italic content in the commands varies depending on your environment.

   .. note::

      For CentOS 6 images, to prevent NIC name drift, you need to create an empty rules configuration file.

      Example:

      **touch /etc/udev/rules.d/**\ *75*\ **-persistent-net-generator.rules** //Replace *75* with the actual value in the environment.

#. Delete network rules.

   -  If the OS uses the initrd system image, perform the following operations:

      a. Run the following command to check whether the initrd image file whose name starts with **initrd** and ends with **default** contains the **persistent** and **net** network device rule files (replace the italic content in the following command with the actual OS version):

         **lsinitrd** **/boot/initrd-**\ *2.6.32.12-0.7*\ **-default** **\|grep** **persistent|grep** **net**

         -  If no, no further action is required.
         -  If yes, go to :ref:`3.b <en-us_topic_0069904570__it_58_45_200040_1_mmccppss_bak>`.

      b. .. _en-us_topic_0069904570__it_58_45_200040_1_mmccppss_bak:

         Run the following command to back up the initrd image files (replace the italic part in the following command with the actual OS version):

         **cp** **/boot/initrd-**\ *2.6.32.12-0.7*\ **-default** **/boot**\ **/**\ **initrd-**\ *2.6.32.12-0.7\ *\ **-**\ **default_bak**

      c. Run the following command to generate the initrd file again:

         **mkinitrd**

   -  If the OS uses the initramfs system image (such as Ubuntu), perform the following operations:

      a. Run the following command to check whether the initramfs image file whose name starts with **initrd** and ends with **generic** contains persistent and net rule files.

         **lsinitramfs** **/boot/initrd.img-3.19.0-25-generic|grep** **persistent|grep** **net**

         -  If no, no further action is required.
         -  If yes, go to :ref:`3.b <en-us_topic_0069904570__li59460586164647>`.

      b. .. _en-us_topic_0069904570__li59460586164647:

         Run the following command to back up the initrd image files:

         **cp** **/boot/initrd.img-3.19.0-25-generic** **/boot/initrd.img-3.19.0-25-generic_bak**

      c. Run the following command to generate the initramfs image files again:

         **update-initramfs -u**
