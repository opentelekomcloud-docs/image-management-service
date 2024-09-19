:original_name: en-us_topic_0171668652.html

.. _en-us_topic_0171668652:

Converting the Image Format Using qemu-img-hw
=============================================

Scenarios
---------

You can import an image file in VHD, VMDK, QCOW2, RAW, VHDX, QCOW, VDI, QED, ZVHD, or ZVHD2 format to the cloud platform. Image files in other formats need to be converted into any of these formats using the open-source tool **qemu-img** before being imported. However, the **qemu-img** tool cannot convert image files to the ZVHD or ZVHD2 format. To convert image files to any of the two formats, use the self-developed tool **qemu-img-hw**. This section describes how to use **qemu-img-hw** to convert an image file to ZVHD2.

Tool and Costs
--------------

.. table:: **Table 1** Tool and costs

   +-----------------------+---------------------------------------------------------------------------------+-----------------------+
   | Tool                  | Description                                                                     | Costs                 |
   +=======================+=================================================================================+=======================+
   | qemu-img-hw           | **qemu-img-hw** is used for converting image formats.                           | Free                  |
   |                       |                                                                                 |                       |
   |                       | You can obtain it from:                                                         |                       |
   |                       |                                                                                 |                       |
   |                       | https://obs-20181128-ims.obs.eu-de.otc.t-systems.com/DT-image-convert-tools.zip |                       |
   +-----------------------+---------------------------------------------------------------------------------+-----------------------+

Constraints
-----------

**qemu-img-hw** can be used only in Linux. You can run it on a local Linux server or a Linux ECS on the cloud platform. The following procedure uses an EulerOS ECS as an example.

Procedure
---------

#. Upload the image file to be converted to the ECS.

   -  If the local host runs a Linux OS, run the **scp** command.

      For example, to upload **image01.qcow2** to the **/usr/** directory of the ECS, run the following command:

      **scp** **/var/image01.qcow2** **root@**\ *xxx.xxx.xx.xxx*\ **:/usr/**

      *xxx.xxx.xx.xxx* indicates the EIP bound to the ECS.

   -  If the local host runs a Windows OS, use a file transfer tool, such as WinSCP, to upload the image file to the ECS.

#. Obtain the **qemu-img-hw** software package, upload it to the ECS, and then decompress the package.

   .. table:: **Table 2** qemu-img-hw package

      +--------------------+---------------------------------------------------------------------------------+
      | Tool Package       | How to Obtain                                                                   |
      +====================+=================================================================================+
      | quick-import-tools | https://obs-20181128-ims.obs.eu-de.otc.t-systems.com/DT-image-convert-tools.zip |
      +--------------------+---------------------------------------------------------------------------------+

   .. note::

      This tool can be used only on x86 servers.

#. Convert the image format.

   a. Go to the directory where **qemu-img-hw** is stored, for example, **/usr/quick-import-tools/qemu-img-hw**.

      **cd** **/usr/quick-import-tools/qemu-img-hw**

   b. Run the following command to change file permissions:

      **chmod** **+x** **qemu-img-hw**

   c. Run the **qemu-img-hw** command to convert the image file to the ZVHD2 format.

      The command format of **qemu-img-hw** is as follows:

      **./qemu-img-hw convert -p -O** *Target_image_format* *Source_image_file* *Target_image_file*

      For example, run the following command to convert an **image01.qcow2** file to an **image01.zvhd2** file:

      **./qemu-img-hw** **convert** **-p** **-O** **zvhd2** **image01.qcow2** **image01.zvhd2**

Appendix 1: Common qemu-img-hw Commands
---------------------------------------

-  Converting image file formats: **qemu-img-hw convert -p -O** *Target_image_format* *Source_image__file* *Target_image_file*

   The parameters are described as follows:

   **-p**: indicates the conversion progress.

   The part following **-O** (which must be in upper case) consists of the target image format, source image file, and target image file.

   For example, run the following command to convert a QCOW2 image file to a ZVHD2 file:

   **qemu-img-hw** **convert** **-p** **-O** **zvhd2** **test.qcow2** **test.zvhd2**

-  Querying image file information: **qemu-img-hw info** *Image file*

   An example command is **qemu-img-hw info test.zvhd2**.

-  Viewing help information: **qemu-img-hw -help**

Appendix 2: Common Errors During qemu-img-hw Running
----------------------------------------------------

-  Symptom:

   The following information is displayed when you run the **qemu-img-hw** command:

   .. code-block::

      ./qemu-img-hw: /lib64/libc.so.6: version `GLIBC_2.14' not found (required by ./qemu-img-hw)

   Solution:

   Run the **strings /lib64/libc.so.6 \| grep glibc** command to check the glibc version. If the version is too early, install the latest version. Run the following commands in sequence:

   **wget** **http://ftp.gnu.org/gnu/glibc/glibc-2.15.tar.gz**

   **wget** **http://ftp.gnu.org/gnu/glibc/glibc-ports-2.15.tar.gz**

   **tar** **-xvf** **glibc-2.15.tar.gz**

   **tar** **-xvf** **glibc-ports-2.15.tar.gz**

   **mv** **glibc-ports-2.15** **glibc-2.15/ports**

   **mkdir** **glibc-build-2.15**

   **cd** **glibc-build-2.15**

   **../glibc-2.15/configure** **--prefix=/usr** **--disable-profile** **--enable-add-ons** **--with-headers=/usr/include** **--with-binutils=/usr/bin**

   .. note::

      If **configure: error: no acceptable C compiler found in $PATH** is displayed, run the **yum -y install gcc** command.

   **make**

   **make** **install**

-  Symptom:

   The following information is displayed when you run the **qemu-img-hw** command:

   .. code-block::

      ./qemu-img-hw: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory

   Solution: Run the **yum install libaio** command.
