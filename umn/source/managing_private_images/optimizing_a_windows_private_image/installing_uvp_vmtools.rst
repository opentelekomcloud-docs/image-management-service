:original_name: en-us_topic_0037352061.html

.. _en-us_topic_0037352061:

Installing UVP VMTools
======================

Scenarios
---------

This section only applies to KVM ECSs, which will replace Xen ECSs gradually. Before using an ECS or external image file to create a private image, ensure that UVP VMTools has been installed in the OS to enable subsequently created ECSs to support KVM virtualization and improve network performance.

.. caution::

   If you do not install UVP VMTools, NICs of the ECS may not be detected and the ECS cannot communicate with other resources.

UVP VMTools has been installed by default when you use a public image to create ECSs. You can perform the following operations to verify the installation:

Open the **version** configuration file to check whether UVP VMTools is the latest:

**C:\\Program Files (x86)\\virtio\\bin\\version**

If the version is 2.5.0 or later, the current UVP VMTools can be used. Otherwise, perform operations in :ref:`Installing UVP VMTools <en-us_topic_0037352061__en-us_topic_0036684065_section12153337>` to install UVP VMTools.

Prerequisites
-------------

-  An EIP has been bound to the ECS.
-  The UVP VMTools installation package has been downloaded on the ECS. For how to obtain the installation package, see :ref:`Obtaining Required Software Packages <en-us_topic_0037352059>`.
-  Ensure that the ECS has at least 50 MB disk space.
-  To avoid an installation failure, perform the following operations before starting the installation:

   -  Uninstall third-party virtualization platform tools, such as Citrix Xen Tools and VMware Tools. For how to uninstall the tools, see the corresponding official documents of the tools.
   -  Disable your antivirus and intrusion detection software. You can enable the software after UVP VMTools is installed.

.. _en-us_topic_0037352061__en-us_topic_0036684065_section12153337:


Installing UVP VMTools
----------------------

The following operations describe how to install UVP VMTools. **vmtools-WIN2016-x64.exe** extracted from **vmtools-WIN2016-x64.zip** is used as an example.

#. Log in to the Windows ECS using VNC.

   For details about how to log in to an ECS, see *Elastic Cloud Server User Guide*.

   .. note::

      You must log in to the ECS using VNC. Remote desktop connection is not allowed because the NIC driver needs to be updated during the installation but the NIC is in use for the remote desktop connection. As a result, the installation will fail.

#. Download the required UVP VMTools based on the ECS OS and :ref:`Obtaining Required Software Packages <en-us_topic_0037352059>`.

#. Decompress the UVP Tools software package **vmtools-WIN2016-x64.zip**.

#. Right-click **vmtools-WIN2016-x64.exe**, and select **Run as administrator** from the shortcut menu.

#. In the displayed dialog box, select **I agree to the license terms and conditions** and click **Install**.


   .. figure:: /_static/images/en-us_image_0000001494625768.png
      :alt: **Figure 1** Installing UVP VMTools

      **Figure 1** Installing UVP VMTools

#. Restart the OS for UVP VMTools to take effect.

#. Perform the operations in :ref:`Verifying the Installation <en-us_topic_0037352061__en-us_topic_0036684065_section42271171>` to check whether UVP VMTools is successfully installed.

.. _en-us_topic_0037352061__en-us_topic_0036684065_section42271171:

Verifying the Installation
--------------------------

Perform the following steps to verify the installation of UVP VMTools:

#. Click **Start**. Choose **Control Panel** > **Programs and Features**.

#. Locate UVP VMTools for Windows.

   If UVP VMTools for Windows exists, the installation is successful, as shown in :ref:`Figure 2 <en-us_topic_0037352061__fig6404346182112>`.

   .. _en-us_topic_0037352061__fig6404346182112:

   .. figure:: /_static/images/en-us_image_0127506675.png
      :alt: **Figure 2** Verifying the installation

      **Figure 2** Verifying the installation
