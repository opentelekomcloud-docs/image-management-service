:original_name: en-us_topic_0030713143.html

.. _en-us_topic_0030713143:

External Image File Formats and Supported OSs
=============================================

External File Formats
---------------------

Image files in VMDK, VHD, QCOW2, RAW, VHDX, QED, VDI, QCOW, ZVHD2, or ZVHD format can be used to create private images. Select the format that best meets your requirements.

Supported OSs
-------------

When you upload an external image file on the management console, the system automatically detects the OS of the image.

If the OS cannot be identified or is not supported:

-  For Windows, **Other_Windows (64_bit)** or **Other_Windows (32_bit)** will be selected during image registration.
-  For Linux, **Other_Linux (64_bit)** or **Other_Linux (32_bit)** will be selected during image registration.

.. note::

   -  Uploading image files containing OSs not listed in :ref:`Table 1 <en-us_topic_0030713143__table33979943151659>` may fail. You are advised to contact the customer service before attempting to upload these image files.
   -  You can only use external image files containing Windows 10 64bit or Windows 7 Enterprise 64bit to create ECSs on a Dedicated Host (DeH).

.. _en-us_topic_0030713143__table33979943151659:

.. table:: **Table 1** Supported OSs (x86)

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | OS                                | Version                                                                                                                                           |
   +===================================+===================================================================================================================================================+
   | Rocky Linux                       | 64-bit: Rocky Linux 9.3/9.2/9.1/9.0                                                                                                               |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Rocky Linux 8.10/8.9/8.8/8.7/8.6/8.5/8.4/8.3                                                                                              |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | AlmaLinux                         | 64-bit: AlmaLinux 9.2/9.1/9.0                                                                                                                     |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: AlmaLinux 8.9/8.8/8.7/8.6/8.5/8.4/8.3                                                                                                     |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Windows                           | 64-bit: Windows Server 2022 Standard/Datacenter                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows Server 2019 Standard/Datacenter                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows Server 2016 Standard/Datacenter                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows Server 2012 R2 Standard/Datacenter                                                                                                |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows Server 2012 Essentials R2                                                                                                         |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows Server 2012 Standard/Datacenter                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows Server 2008 WEB R2                                                                                                                |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows Server 2008 R2 Standard/Datacenter                                                                                                |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows Server 2008 R2 Enterprise                                                                                                         |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows 11                                                                                                                                |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Windows 10                                                                                                                                |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | SUSE                              | 64-bit: SUSE Linux Enterprise Server 15 SP5/15 SP4/15 SP3/15 SP2/15 SP1/15                                                                        |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: SUSE Linux Enterprise Server 12 SP5/12 SP4/12 SP3/12 SP2/12 SP1/12                                                                        |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: SUSE Linux Enterprise Server 11 SP4/11 SP3/11                                                                                             |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Oracle Linux                      | 64-bit: Oracle Linux Server release 9.4/9.3/9.2/9.1/9.0                                                                                           |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Oracle Linux Server release 8.9/8.8/8.7/8.6/8.5/8.4/8.3/8.2/8.1/8.0                                                                       |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Oracle Linux Server release 7.9/7.8/7.7/7.6/7.5/7.4/7.3/7.2/7.1/7.0                                                                       |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Oracle Linux Server release 6.10/6.9/6.8/6.7/6.5                                                                                          |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Red Hat                           | 64-bit: Red Hat Linux Enterprise 9.4/9.3/9.2/9.1/9.0                                                                                              |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Red Hat Linux Enterprise 8.7/8.6/8.5/8.4/8.3/8.2/8.1/8.0                                                                                  |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Red Hat Linux Enterprise 7.9/7.8/7.7/7.6/7.5/7.4/7.3/7.2/7.1/7.0                                                                          |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Red Hat Linux Enterprise 6.10/6.9/6.8/6.7/6.6/6.5/6.4                                                                                     |
   |                                   |                                                                                                                                                   |
   |                                   | 32-bit: Red Hat Linux Enterprise 6.4                                                                                                              |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Ubuntu                            | 64-bit: Ubuntu 22.04/20.04/19.04/18.04.2/18.04.1/18.04/16.04.6/16.04.5/16.04.4/16.04.3/16.04.2/16.04/14.04.5/14.04.4/14.04.3/14.04.1/14.04 Server |
   |                                   |                                                                                                                                                   |
   |                                   | 32-bit: Ubuntu 14.04.4/14.04.3/14.04.1/14.0 Server                                                                                                |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | openSUSE                          | 64-bit: openSUSE 42.3/42.2/42.1                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: openSUSE 15.5/15.4/15.3/15.2/15.0/13.2/11.3                                                                                               |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | CentOS                            | 64-bit: CentOS 8.3/8.2/8.1/8.0                                                                                                                    |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: CentOS 7.9/7.8/7.7/7.6/7.5/7.4/7.3/7.2/7.1/7.0                                                                                            |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: CentOS 6.10/6.9/6.8/6.7/6.6/6.5/6.4/6.3                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | 32-bit: CentOS 7.0                                                                                                                                |
   |                                   |                                                                                                                                                   |
   |                                   | 32-bit: CentOS 6.10/6.7/6.6/6.5/6.4/6.3                                                                                                           |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Debian                            | 64-bit: Debian GNU/Linux 12.5.0/12.4.0/12.3.0/12.2.0/12.1.0/12.0.0                                                                                |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Debian GNU/Linux 11.9.0/11.8.0/11.7.0/11.6.0/11.5.0/11.4.0/11.3.0/11.2.0/11.1.0/11.0.0                                                    |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Debian GNU/Linux 10.13.0/10.12.0/10.11.0/10.10.0/10.9.0/10.8.0/10.7.0/10.6.0/10.5.0/10.4.0/10.3.0/10.2.0/10.1.0/10.0.0                    |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Debian GNU/Linux 9.13.0/9.3.0/9.0.0                                                                                                       |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Debian GNU/Linux 8.8.0/8.7.0/8.6.0/8.5.0/8.4.0/8.2.0/8.1.0                                                                                |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Fedora                            | 64-bit: Fedora 34/33/32/31/30                                                                                                                     |
   |                                   |                                                                                                                                                   |
   |                                   | 64-bit: Fedora 29/28/27/26/25/24/23/22                                                                                                            |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | EulerOS                           | 64-bit: EulerOS 2.10/2.9/2.7/2.5/2.3/2.2/2.1                                                                                                      |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | CoreOS                            | CoreOS 1800.1.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1745.2.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1632.0.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1520.8.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1465.8.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1298.5.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1122.3.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1122.2.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1185.5.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1068.10.0                                                                                                                                  |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1010.5.0                                                                                                                                   |
   |                                   |                                                                                                                                                   |
   |                                   | CoreOS 1298.6.0                                                                                                                                   |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | openEuler                         | 64-bit: openEuler 24.03/22.03 SP4/22.03 SP3/22.03 SP2/22.03 SP1/22.03/20.03 SP3/20.03 SP2/20.03 SP1/20.03                                         |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Related Operations
------------------

For how to upload an external image file, see :ref:`Uploading an Image File <en-us_topic_0030713183>` and :ref:`Uploading an Image File <en-us_topic_0030713192>`.

After an external image file is successfully uploaded, you can register this image file as a private image on the cloud platform. For details, see :ref:`Registering an Image File as a Private Image <en-us_topic_0030713184>` and :ref:`Registering an Image File as a Private Image <en-us_topic_0030713193>`.
