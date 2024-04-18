:original_name: en-us_topic_0030713143.html

.. _en-us_topic_0030713143:

External Image File Formats and Supported OSs
=============================================

External File Formats
---------------------

Image files in VMDK, VHD, QCOW2, RAW, VHDX, QED, VDI, QCOW, ZVHD2, or ZVHD format can be used to create private images. Select whichever format best meeting your requirements.

Supported OSs
-------------

When you upload an external image file to an OBS bucket on the management console, the OS contained in the image file will be checked. :ref:`Table 1 <en-us_topic_0030713143__table6432073491848>` lists the OSs supported by external image files.

If the OS cannot be identified or is not supported:

-  For Windows, **Other_Windows (64_bit)** or **Other_Windows (32_bit)** will be selected during image registration.
-  For Linux, **Other_Linux (64_bit)** or **Other_Linux (32_bit)** will be selected during image registration.

.. note::

   -  Uploading image files containing OSs not listed in :ref:`Table 1 <en-us_topic_0030713143__table6432073491848>` may fail. You are advised to contact the customer service before uploading these image files.
   -  For details about the formats and OSs supported for BMS images, see *Bare Metal Server Private Image Creation Guide*.
   -  When uploading a CoreOS image file, set the OS type to CoreOS. Otherwise, the OS type will be set to **Other (64bit)**. In addition, ensure that coreos-cloudinit has been installed and configured for CoreOS. Automatic system upgrades must be disabled. Otherwise, they may make ECSs created using this image unavailable.
   -  You can only use external image files containing Windows 10 64bit or Windows 7 Enterprise 64bit to create ECSs on a Dedicated Host (DeH).

.. _en-us_topic_0030713143__table6432073491848:

.. table:: **Table 1** Supported OSs

   +-----------------------------------+-------------------------------------------+
   | OS                                | Version                                   |
   +===================================+===========================================+
   | Windows                           | Windows 10 64bit                          |
   |                                   |                                           |
   |                                   | Windows 7 Enterprise 64bit                |
   |                                   |                                           |
   |                                   | Windows 7 Professional 64bit              |
   |                                   |                                           |
   |                                   | Windows 7 Professional 32bit              |
   |                                   |                                           |
   |                                   | Windows Server 2016 Standard 64bit        |
   |                                   |                                           |
   |                                   | Windows Server 2016 Datacenter 64bit      |
   |                                   |                                           |
   |                                   | Windows Server 2012 R2 Standard 64bit     |
   |                                   |                                           |
   |                                   | Windows Server 2012 R2 Essentials 64bit   |
   |                                   |                                           |
   |                                   | Windows Server 2012 R2 Datacenter 64bit   |
   |                                   |                                           |
   |                                   | Windows Server 2012 Datacenter 64bit      |
   |                                   |                                           |
   |                                   | Windows Server 2012 Standard 64bit        |
   |                                   |                                           |
   |                                   | Windows Server 2008 WEB R2 64bit          |
   |                                   |                                           |
   |                                   | Windows Server 2008 R2 Standard 64bit     |
   |                                   |                                           |
   |                                   | Windows Server 2008 R2 Enterprise 64bit   |
   |                                   |                                           |
   |                                   | Windows Server 2008 R2 Datacenter 64bit   |
   +-----------------------------------+-------------------------------------------+
   | SUSE                              | SUSE Linux Enterprise Server 15 SP1 64bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 15 64bit     |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 12 SP5 64bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 12 SP4 64bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 12 SP3 64bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 12 SP2 64bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 12 SP1 64bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 12 64bit     |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 11 SP4 64bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 11 SP3 64bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 11 SP3 32bit |
   |                                   |                                           |
   |                                   | SUSE Linux Enterprise Server 11 SP1 32bit |
   +-----------------------------------+-------------------------------------------+
   | Oracle Linux                      | Oracle Linux Server release 7.6 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 7.5 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 7.4 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 7.3 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 7.2 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 7.1 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 7.0 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 6.10 64bit    |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 6.9 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 6.8 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 6.7 64bit     |
   |                                   |                                           |
   |                                   | Oracle Linux Server release 6.5 64bit     |
   +-----------------------------------+-------------------------------------------+
   | Red Hat                           | Red Hat Linux Enterprise 8.0 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 7.6 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 7.5 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 7.4 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 7.3 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 7.2 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 7.1 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 7.0 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.10 64bit       |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.9 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.8 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.7 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.6 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.6 32bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.5 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.4 64bit        |
   |                                   |                                           |
   |                                   | Red Hat Linux Enterprise 6.4 32bit        |
   +-----------------------------------+-------------------------------------------+
   | Ubuntu                            | Ubuntu 20.04 Server 64bit                 |
   |                                   |                                           |
   |                                   | Ubuntu 19.04 Server 64bit                 |
   |                                   |                                           |
   |                                   | Ubuntu 18.04.2 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 18.04.1 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 18.04 Server 64bit                 |
   |                                   |                                           |
   |                                   | Ubuntu 16.04.6 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 16.04.5 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 16.04.4 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 16.04.3 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 16.04.2 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 16.04 Server 64bit                 |
   |                                   |                                           |
   |                                   | Ubuntu 14.04.5 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 14.04.4 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 14.04.4 Server 32bit               |
   |                                   |                                           |
   |                                   | Ubuntu 14.04.3 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 14.04.3 Server 32bit               |
   |                                   |                                           |
   |                                   | Ubuntu 14.04.1 Server 64bit               |
   |                                   |                                           |
   |                                   | Ubuntu 14.04.1 Server 32bit               |
   |                                   |                                           |
   |                                   | Ubuntu 14.04 Server 64bit                 |
   |                                   |                                           |
   |                                   | Ubuntu 14.04 Server 32bit                 |
   +-----------------------------------+-------------------------------------------+
   | openSUSE                          | openSUSE 42.3 64bit                       |
   |                                   |                                           |
   |                                   | openSUSE 42.2 64bit                       |
   |                                   |                                           |
   |                                   | openSUSE 42.1 64bit                       |
   |                                   |                                           |
   |                                   | openSUSE 15.1 64bit                       |
   |                                   |                                           |
   |                                   | openSUSE 15.0 64bit                       |
   |                                   |                                           |
   |                                   | openSUSE 13.2 64bit                       |
   |                                   |                                           |
   |                                   | openSUSE 11.3 64bit                       |
   +-----------------------------------+-------------------------------------------+
   | CentOS                            | CentOS 8.0 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.9 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.8 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.7 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.6 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.5 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.4 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.3 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.2 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.1 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.0 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 7.0 32bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.10 64bit                         |
   |                                   |                                           |
   |                                   | CentOS 6.10 32bit                         |
   |                                   |                                           |
   |                                   | CentOS 6.9 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.8 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.7 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.7 32bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.6 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.6 32bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.5 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.5 32bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.4 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.4 32bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.3 64bit                          |
   |                                   |                                           |
   |                                   | CentOS 6.3 32bit                          |
   +-----------------------------------+-------------------------------------------+
   | Debian                            | Debian GNU/Linux 10.0.0 64bit             |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 9.3.0 64bit              |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 9.0.0 64bit              |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 8.8.0 64bit              |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 8.7.0 64bit              |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 8.6.0 64bit              |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 8.5.0 64bit              |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 8.4.0 64bit              |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 8.2.0 64bit              |
   |                                   |                                           |
   |                                   | Debian GNU/Linux 8.1.0 64bit              |
   +-----------------------------------+-------------------------------------------+
   | Fedora                            | Fedora 30 64bit                           |
   |                                   |                                           |
   |                                   | Fedora 29 64bit                           |
   |                                   |                                           |
   |                                   | Fedora 28 64bit                           |
   |                                   |                                           |
   |                                   | Fedora 27 64bit                           |
   |                                   |                                           |
   |                                   | Fedora 26 64bit                           |
   |                                   |                                           |
   |                                   | Fedora 25 64bit                           |
   |                                   |                                           |
   |                                   | Fedora 24 64bit                           |
   |                                   |                                           |
   |                                   | Fedora 23 64bit                           |
   |                                   |                                           |
   |                                   | Fedora 22 64bit                           |
   +-----------------------------------+-------------------------------------------+
   | EulerOS                           | EulerOS 2.9 64bit                         |
   |                                   |                                           |
   |                                   | EulerOS 2.5 64bit                         |
   |                                   |                                           |
   |                                   | EulerOS 2.3 64bit                         |
   |                                   |                                           |
   |                                   | EulerOS 2.2 64bit                         |
   |                                   |                                           |
   |                                   | EulerOS 2.1 64bit                         |
   +-----------------------------------+-------------------------------------------+
   | CoreOS                            | CoreOS 1068.10.0                          |
   |                                   |                                           |
   |                                   | CoreOS 1010.5.0                           |
   |                                   |                                           |
   |                                   | CoreOS 1298.6.0                           |
   +-----------------------------------+-------------------------------------------+
   | openEuler                         | openEuler 20.03 64bit                     |
   +-----------------------------------+-------------------------------------------+

Related Operations
------------------

For how to upload an external image file, see :ref:`Uploading an External Image File <en-us_topic_0030713183>` and :ref:`Uploading an External Image File <en-us_topic_0030713192>`.

After an external image file is successfully uploaded, you can register this image file as a private image on the cloud platform. For details, see :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713184>` and :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713193>`.
