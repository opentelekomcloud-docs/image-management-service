:original_name: en-us_topic_0030713185.html

.. _en-us_topic_0030713185:

What Do I Do If a Windows Image File Is Not Pre-Configured When I Use It to Register a Private Image?
=====================================================================================================

If an image file is not configured as instructed in :ref:`Table 1 <en-us_topic_0030713189__table85212269215>` before it is exported from the original platform, configure it by referring to :ref:`Figure 1 <en-us_topic_0030713185__fig18196115421120>`.

.. caution::

   The proper running of ECSs depends on the KVM Guest OS driver (UVP VMTools), without which the performance of ECSs will be affected and some functions will be unavailable. Ensure that the driver installation has been completed for the image file before it is exported from the original platform. Otherwise, the ECSs created from the image will fail to start.

   For details about how to install UVP VMTools, see :ref:`Installing UVP VMTools <en-us_topic_0037352061>`.

.. _en-us_topic_0030713185__fig18196115421120:

.. figure:: /_static/images/en-us_image_0208476701.png
   :alt: **Figure 1** Image creation process

   **Figure 1** Image creation process

.. _en-us_topic_0030713185__section1049514242043:

Step 1: Upload the Image File
-----------------------------

Upload the external image file to an OBS bucket. For details, see :ref:`Uploading an External Image File <en-us_topic_0030713183>`.

.. _en-us_topic_0030713185__section4198749842:

Step 2 Register the Image File as a Private Image
-------------------------------------------------

On the management console, select the uploaded image file and register it as a private image. For details, see :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713184>`.

.. _en-us_topic_0030713185__en-us_topic_0029124475_s3524cdcb025c4c3aa892d8c644fc677e:

Step 3: Create an ECS
---------------------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Computing**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab.

#. Locate the row that contains the private image and click **Apply for Server** in the **Operation** column.

#. Set parameters as promoted to create an ECS. Pay attention to the following:

   -  Bind an EIP to the ECS so that you can upload installation packages to the ECS or download installation packages from the ECS.
   -  You must add inbound rules for security groups of the ECS to ensure that the ECS can be accessed.
   -  If the image file has Cloudbase-Init installed, set a password and log in to the ECS using the password as prompted. If Cloudbase-Init is not installed, use the password or certificate contained in the image file to log in the ECS.

   For details, see *Elastic Cloud Server User Guide*.

#. Perform the following steps to check whether the private image has been pre-configured:

   a. Check whether the ECS can be successfully started. If the start succeeds, a Guest OS driver has been installed for the image file on the original platform or the driver has been automatically installed for the private image on the cloud platform. If the start failed, install a Guest OS driver for the image file on the original platform and start from :ref:`Step 1: Upload the Image File <en-us_topic_0030713185__section1049514242043>` again.
   b. Check whether you can log in to the ECS using your configured password or key. If you can, Cloudbase-Init has been installed. If you cannot, use the password or key contained in the image file to log in to the ECS and install Cloudbase-Init as instructed in :ref:`Installing and Configuring Cloudbase-Init <en-us_topic_0030730602>`.
   c. Check whether NICs are set to DHCP by referring to :ref:`2 <en-us_topic_0030713185__li19785161610328>` in :ref:`Step 4: Configure the ECS <en-us_topic_0030713185__section1170711344016>`.
   d. Use MSTSC to log in to the ECS. If the login is successful, remote desktop connection is enabled on the ECS. If the login fails, enable remote desktop connection by referring to :ref:`3 <en-us_topic_0030713185__li174414479612>` in :ref:`Step 4: Configure the ECS <en-us_topic_0030713185__section1170711344016>`.

   If the ECS meets the preceding requirements, the private image has been pre-configured. Skip :ref:`Step 4: Configure the ECS <en-us_topic_0030713185__section1170711344016>` and :ref:`Step 5: Create a Private Image from the ECS <en-us_topic_0030713185__section10407615356>`.

.. _en-us_topic_0030713185__section1170711344016:

Step 4: Configure the ECS
-------------------------

Remotely log in to the ECS created in :ref:`Step 3: Create an ECS <en-us_topic_0030713185__en-us_topic_0029124475_s3524cdcb025c4c3aa892d8c644fc677e>` to configure it.

#. Log in to the ECS.

#. .. _en-us_topic_0030713185__li19785161610328:

   Check whether NICs are set to DHCP. If the ECS is configured with a static IP address, change its IP address assignment mode to DHCP as instructed in :ref:`Setting the NIC to DHCP <en-us_topic_0030713152>`.

#. .. _en-us_topic_0030713185__li174414479612:

   Enable remote desktop connection for the ECS as needed. For details about how to enable this function, see :ref:`Enabling Remote Desktop Connection <en-us_topic_0030713155>`.

#. (Optional) Configure value-added functions.

   -  Install and configure Cloudbase-Init. For details, see :ref:`Installing and Configuring Cloudbase-Init <en-us_topic_0030730602>`.
   -  Enable NIC multi-queue. For details, see :ref:`How Do I Enable NIC Multi-Queue for an Image? <en-us_topic_0085214115>`

.. _en-us_topic_0030713185__section10407615356:

Step 5: Create a Private Image from the ECS
-------------------------------------------

For details, see :ref:`Creating a System Disk Image from a Windows ECS <en-us_topic_0030713149>`.

(Optional) Clear the Environment
--------------------------------

After the image registration is complete, delete the image file as well as the intermediate private image and ECS to prevent them from occupying storage and compute resources.

-  Delete the image registered in :ref:`Step 2 Register the Image File as a Private Image <en-us_topic_0030713185__section4198749842>`.
-  Delete the ECS created in :ref:`Step 3: Create an ECS <en-us_topic_0030713185__en-us_topic_0029124475_s3524cdcb025c4c3aa892d8c644fc677e>`.
-  Delete the image file from the OBS bucket.
