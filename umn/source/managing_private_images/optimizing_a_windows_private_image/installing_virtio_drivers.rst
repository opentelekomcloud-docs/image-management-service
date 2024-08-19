:original_name: en-us_topic_0000001841305273.html

.. _en-us_topic_0000001841305273:

Installing VirtIO Drivers
=========================

Scenarios
---------

This section only applies to KVM ECSs, which will replace Xen ECSs gradually. Before using an ECS or external image file to create a private image, ensure that VirtIO drivers have been installed in the OS so that ECSs created from this image can support KVM virtualization and the network performance can be improved.

.. caution::

   If you do not install VirtIO drivers, ECS NICs cannot be detected. As a result, the ECSs cannot communicate with other resources.

If an ECS is created from a public image, VirtIO drivers have been installed by default.

Prerequisites
-------------

An EIP has been bound to the ECS. (This ECS is used to optimize a private image.)


Installing VirtIO Drivers
-------------------------

The following uses **virtio-win-gt-x64.msi** in **version virtio-win-0.1.189-1** as an example to describe how to install VirtIO drivers.

#. Log in to the Windows ECS using VNC.

   For details about how to log in to an ECS, see *Elastic Cloud Server User Guide*.

   .. note::

      You must log in to the ECS using VNC. Remote desktop connection is not allowed because the NIC driver needs to be updated during the installation but the NIC is in use for the remote desktop connection. As a result, the installation will fail.

#. Download a VirtIO driver package (**virtio-win-gt-x64.msi** as an example) of the required version by referring to :ref:`Obtaining Required Software Packages <en-us_topic_0037352059>`.


   .. figure:: /_static/images/en-us_image_0000001890826049.png
      :alt: **Figure 1** Downloading a driver package

      **Figure 1** Downloading a driver package

#. After the download is complete, right-click **virtio-win-gt-x64.msi** and choose **Run as administrator** from the shortcut menu.


   .. figure:: /_static/images/en-us_image_0000001842239205.png
      :alt: **Figure 2** Starting the installation

      **Figure 2** Starting the installation


   .. figure:: /_static/images/en-us_image_0000001842120221.png
      :alt: **Figure 3** Installation wizard

      **Figure 3** Installation wizard


   .. figure:: /_static/images/en-us_image_0000001842120669.png
      :alt: **Figure 4** Accepting the agreement

      **Figure 4** Accepting the agreement

   Select the VirtIO drivers to be installed. In this example, select all VirtIO drivers.


   .. figure:: /_static/images/en-us_image_0000001842240965.png
      :alt: **Figure 5** Selecting VirtIO drivers to install

      **Figure 5** Selecting VirtIO drivers to install


   .. figure:: /_static/images/en-us_image_0000001795641858.png
      :alt: **Figure 6** Proceeding with the installation.

      **Figure 6** Proceeding with the installation.

#. Wait until the installation is complete.


   .. figure:: /_static/images/en-us_image_0000001842117653.png
      :alt: **Figure 7** Installation in process

      **Figure 7** Installation in process

#. Restart the ECS after the installation is complete.


   .. figure:: /_static/images/en-us_image_0000001795638722.png
      :alt: **Figure 8** Installation completed

      **Figure 8** Installation completed


   .. figure:: /_static/images/en-us_image_0000001795638958.png
      :alt: **Figure 9** Restart prompt

      **Figure 9** Restart prompt

#. After the restart, perform the operations in :ref:`Verifying the Installation <en-us_topic_0000001841305273__section2835483332>` to verify that the VirtIO drivers have been successfully installed.

.. _en-us_topic_0000001841305273__section2835483332:

Verifying the Installation
--------------------------

Perform the following steps to verify the installation of the VirtIO drivers:

#. Open **Device Manager** and search for VirtIO drivers.

#. Check whether the VirtIO driver version and date displayed in **Device Manager** are the same as those of the VirtIO drivers you downloaded. If they are the same, the VirtIO drivers have been installed successfully.


   .. figure:: /_static/images/en-us_image_0000001795626446.png
      :alt: **Figure 10** Version and date of downloaded drivers

      **Figure 10** Version and date of downloaded drivers


   .. figure:: /_static/images/en-us_image_0000001842227233.png
      :alt: **Figure 11** Version and date of drivers in Device Manager

      **Figure 11** Version and date of drivers in Device Manager
