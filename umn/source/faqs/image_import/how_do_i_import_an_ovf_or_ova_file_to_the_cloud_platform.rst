:original_name: en-us_topic_0118990097.html

.. _en-us_topic_0118990097:

How Do I Import an OVF or OVA File to the Cloud Platform?
=========================================================

Scenarios
---------

Open Virtualization Appliance (OVA) is a single file archive (with the .ova extension) of all of the files comprising an Open Virtualization Format (OVF) package. OVF is a package of the files required for defining and deploying VMs. An OVF package generally includes .ovf, .mf, and .vmdk files.

-  An .ovf file is an XML descriptor that defines the metadata of a VM, such as the name and hardware requirements, and contains information about other files in the OVF package.
-  An .mf file contains the SHA hash codes of all the files in the package and is used to prevent the image file from being tampered with.
-  A .vmdk file is a virtual disk file that is used to create a disk image. An OVF package may contain multiple .vmdk files.

This section describes how to import OVF and OVA files to the cloud platform.

Procedure
---------

Manually extract VMDK files from an OVF or OVA template and upload them to an OBS bucket. Then, you can select one of them from the bucket when you use an external file to create a system or data disk image.

.. note::

   The following assumes that the OVF or OVA template contains only one VMDK file. If there are multiple VMDK files (for example, there are three VMDK files, one used as a system disk image file and the others as data disk image files), upload them to an OBS bucket and register them as a system disk image and data disk images, respectively.

-  The source VM runs Windows.

   -  If you choose to export an OVF template named **MyVm** and save it to the **OvfLib** folder in drive C, the following files will be generated in the folder (the VMDK file can be uploaded to the cloud platform):

      .. code-block::

         ├C
         │  ├OvfLib
         │       ├MyVm
         │          ├MyVm.ovf
         │       ├MyVm.mf
         │       ├MyVm-disk1.vmdk

   -  If you choose to export an OVA template and name it **MyVm**, the **C:\\MyVm.ova** file will be generated. The VMDK file extracted from **MyVm.ova** can be uploaded to the cloud platform.

      .. note::

         You can import an image file in VHD, VMDK, QCOW2, RAW, VHDX, QCOW, VDI, QED, ZVHD, or ZVHD2 format to create a private image.

   For details, see :ref:`Creating a Windows System Disk Image from an External Image File <en-us_topic_0030713181>` or :ref:`Creating a Data Disk Image from an External Image File <en-us_topic_0084064672>`.

-  The source VM runs Linux.

   -  If you choose to export an OVF template, upload the VMDK file generated in the folder to the cloud platform.
   -  If you choose to export an OVA template and name it **MyVm**, perform the following operations:

      #. Run the following command to check the OVA file:

         **file MyVm.ova**

         The command output is as follows:

         .. code-block::

            MyVm.ova: POSIX tar archive (GNU)

         **MyVm.ova** contains the following two files:

         .. code-block::

            $tar tf MyVm.ova
            MyVm.ovf
            MyVm.vmdk

      #. Run the following command to decompress **MyVm.ova**:

         **tar xvf MyVm.ova**

         The extracted folder contains the following files:

         .. code-block::

            MyVm.ovf
            MyVm.vmdk

         The .vmdk image file can be uploaded to the cloud platform.

         .. note::

            You can import an image file in the VHD, VMDK, QCOW2, RAW, VHDX, QCOW, VDI, QED, ZVHD, or ZVHD2 format to create a private image.

   For details, see :ref:`Creating a Linux System Disk Image from an External Image File <en-us_topic_0030713190>` or :ref:`Creating a Data Disk Image from an External Image File <en-us_topic_0084064672>`.
