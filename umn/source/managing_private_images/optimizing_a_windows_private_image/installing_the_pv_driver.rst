:original_name: en-us_topic_0037352182.html

.. _en-us_topic_0037352182:

Installing the PV Driver
========================

Scenarios
---------

When using an ECS or external image file to create a private image, ensure that the PV driver has been installed in the OS to enable Xen virtualization for subsequently created ECSs, improve the I/O processing performance of the ECSs, and implement advanced functions such as monitoring hardware of the ECSs.

.. caution::

   If you do not install the PV driver, the ECS network performance will be poor, and the security group and firewall configured for the ECS will not take effect.

The PV driver has been installed by default when you use a public image to create ECSs. You can perform the following operations to verify the installation:

Open the **version** configuration file to check whether the PV driver is the latest:

**C:\Program Files (x86)\Xen PV Drivers\bin\version**

-  If the PV driver version is later than 2.5, you do not need to install the PV driver.
-  If the PV driver version is not displayed or the version is 2.5 or earlier, perform operations in :ref:`Installing the PV Driver <en-us_topic_0037352182__en-us_topic_0036684067_section46181951>`.

Prerequisites
-------------

-  An OS has been installed for the ECS, and an EIP has been bound to the ECS.
-  The remaining capacity of the ECS system disk must be greater than 32 MB.
-  If the ECS uses Windows 2008, you must install the PV driver using the administrator account.
-  The PV driver software package has been downloaded on the ECS. For how to obtain the software package, see :ref:`Obtaining Required Software Packages <en-us_topic_0037352059>`.
-  To avoid an installation failure, perform the following operations before starting the installation:

   -  Uninstall third-party virtualization platform tools, such as Citrix Xen Tools and VMware Tools. For how to uninstall the tools, see the corresponding official documents of the tools.
   -  Disable your antivirus and intrusion detection software. You can enable the software after the PV driver is installed.

.. _en-us_topic_0037352182__en-us_topic_0036684067_section46181951:


Installing the PV Driver
------------------------

#. Log in to the Windows ECS using VNC.

   For details about how to log in to an ECS, see *Elastic Cloud Server User Guide*.

   .. note::

      You must log in to the ECS using VNC. Remote desktop connection is not allowed because the NIC driver needs to be updated during the installation but the NIC is in use for the remote desktop connection. As a result, the installation will fail.

#. On the ECS, choose **Start** > **Control Panel**.

#. Click **Uninstall a program**.

#. Uninstall **GPL PV drivers for Windows** *x.x.x.xx* as prompted.

#. Download the required PV driver based on the ECS OS and :ref:`Obtaining Required Software Packages <en-us_topic_0037352059>`.

#. Decompress the PV driver software package.

#. Right-click **GPL PV Drivers for Windows** *x.x.x.xx*, select **Run as administrator**, and complete the installation as prompted.

#. Restart the ECS as prompted to make the PV driver take effect.

   ECSs running Windows Server 2008 must be restarted twice.

   .. note::

      After the PV driver is installed, the ECS NIC configuration will be lost. If you have configured NICs before, you need to configure them again.

Verifying the Installation
--------------------------

Perform the following steps to verify the installation of the PV driver:

#. Click **Start**. Choose **Control Panel** > **Programs and Features**.

#. Locate the PV driver for Windows.

   If the PV driver exists, the installation is successful, as shown in :ref:`Figure 1 <en-us_topic_0037352182__fig16926124855714>`.

   .. _en-us_topic_0037352182__fig16926124855714:

   .. figure:: /_static/images/en-us_image_0219481382.png
      :alt: **Figure 1** Verifying the installation


      **Figure 1** Verifying the installation
