:original_name: en-us_topic_0146474784.html

.. _en-us_topic_0146474784:

Installing a Windows OS and VirtIO Drivers
==========================================

Scenarios
---------

This section uses Windows Server 2019 64-bit as an example to describe how to install Windows on an ECS.

The installation procedure varies depending on the image file you use. Perform operations as prompted.

.. note::

   Set the time zone, KMS address, patch server, input method, and language based on service requirements.

Prerequisites
-------------

You have remotely logged in to the ECS and entered the installation page.

Procedure
---------

.. caution::

   Do not stop or restart the ECS during the OS installation. Otherwise, the OS installation will fail.

#. Install the Windows OS.

   a. Configure Windows setup.


      .. figure:: /_static/images/en-us_image_0000001829389966.png
         :alt: **Figure 1** Windows setup

         **Figure 1** Windows setup

   b. Click **Next**.

      The installation confirmation window is displayed.


      .. figure:: /_static/images/en-us_image_0000001829550782.png
         :alt: **Figure 2** Installation confirmation

         **Figure 2** Installation confirmation

   c. Click **Install now**.

      The **Select the operating system you want to install** dialog box is displayed.

   d. Select the version of the OS to be installed and click **Next**.

      The **Please read the license terms** dialog box is displayed.

   e. Select **I accept the license terms**, and click **Next**.

      The **Which type of installation do you want?** dialog box is displayed.


      .. figure:: /_static/images/en-us_image_0146478947.png
         :alt: **Figure 3** Installation type

         **Figure 3** Installation type

   f. Select **Custom (advanced)**.

      The **Where do you want to install Windows?** dialog box is displayed.

      -  If the system displays a message indicating that no driver is found, go to :ref:`1.g <en-us_topic_0146474784__li2827143133314>`.


         .. figure:: /_static/images/en-us_image_0000001860980389.png
            :alt: **Figure 4** Installation path

            **Figure 4** Installation path

      -  If a disk is displayed, go to :ref:`1.i <en-us_topic_0146474784__li98272043173314>`.


         .. figure:: /_static/images/en-us_image_0160277966.png
            :alt: **Figure 5** Installation path

            **Figure 5** Installation path

   g. .. _en-us_topic_0146474784__li2827143133314:

      Click **Load driver** and then **Browse**.


      .. figure:: /_static/images/en-us_image_0160277608.png
         :alt: **Figure 6** Loading drivers

         **Figure 6** Loading drivers

   h. Select a driver based on the disk type.

      -  If the disk type is VBD, choose **viostor** > **2k19** > **amd64** and click **OK**.


         .. figure:: /_static/images/en-us_image_0000001979249001.png
            :alt: **Figure 7** Browsing for a folder

            **Figure 7** Browsing for a folder

         Select the **viostor.inf** driver and click **Next**.


         .. figure:: /_static/images/en-us_image_0000001948967564.png
            :alt: **Figure 8** Selecting the driver to install

            **Figure 8** Selecting the driver to install

      -  If the disk type is SCSI, choose **vioscsi** > **2k19** > **amd64** and click **OK**.


         .. figure:: /_static/images/en-us_image_0000001979408863.png
            :alt: **Figure 9** Browsing for a folder

            **Figure 9** Browsing for a folder

         Select the **vioscsi.inf** driver and click **Next**.


         .. figure:: /_static/images/en-us_image_0000001978685553.png
            :alt: **Figure 10** Selecting the driver to install

            **Figure 10** Selecting the driver to install

   i. .. _en-us_topic_0146474784__li98272043173314:

      Select the disk and click **Next**.


      .. figure:: /_static/images/en-us_image_0146478949.png
         :alt: **Figure 11** Installation path

         **Figure 11** Installation path

      .. note::

         If the disk type is **Offline**, you can stop and then start the ECS, and restart the OS installation process.


         .. figure:: /_static/images/en-us_image_0160826569.png
            :alt: **Figure 12** Offline disk

            **Figure 12** Offline disk

   j. The **Installing Windows** dialog box is displayed, and the OS installation starts.

      The installation takes about 50 minutes. The ECS restarts during the installation. After the ECS successfully restarts, log in to it again and configure the OS as prompted.

      .. note::

         You are required to set a password for the OS user.

         Supported special characters include ``!@$%^-_=+[{}]:,./?``


      .. figure:: /_static/images/en-us_image_0146478951.png
         :alt: **Figure 13** Installation progress

         **Figure 13** Installation progress

#. Install drivers.

   a. Open **Computer** and double-click the CD drive.


      .. figure:: /_static/images/en-us_image_0000001860906473.png
         :alt: **Figure 14** Starting the CD drive

         **Figure 14** Starting the CD drive

   b. Double-click **virtio-win-gt-x64** or **virtio-win-gt-x86**. Install drivers as prompted.

   c. After the installation is complete, start **Device Manager** and check that all the drivers shown in the red box are successfully installed.


      .. figure:: /_static/images/en-us_image_0160278272.png
         :alt: **Figure 15** Device Manager

         **Figure 15** Device Manager
