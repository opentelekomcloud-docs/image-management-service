:original_name: en-us_topic_0146474784.html

.. _en-us_topic_0146474784:

Installing a Windows OS and the VMTools Driver
==============================================

Scenarios
---------

This section uses Windows Server 2008 R2 64-bit as an example to describe how to install Windows on an ECS.

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

   a. Specify the parameters on the **Install Windows** page.


      .. figure:: /_static/images/en-us_image_0146478919.png
         :alt: **Figure 1** Install Windows

         **Figure 1** Install Windows

   b. Click **Next**.

      The installation confirmation window is displayed.


      .. figure:: /_static/images/en-us_image_0146478941.png
         :alt: **Figure 2** Installation confirmation window

         **Figure 2** Installation confirmation window

   c. Click **Install now**.

      The **Select the operating system you want to install** window is displayed.


      .. figure:: /_static/images/en-us_image_0146478943.png
         :alt: **Figure 3** Selecting the OS version

         **Figure 3** Selecting the OS version

   d. Select the version of the OS to be installed and click **Next**.

      The **Please read the license terms** window is displayed.


      .. figure:: /_static/images/en-us_image_0146478945.png
         :alt: **Figure 4** License terms window

         **Figure 4** License terms window

   e. Select **I accept the license terms**, and click **Next**.

      The **Which type of installation do you want?** window is displayed.


      .. figure:: /_static/images/en-us_image_0146478947.png
         :alt: **Figure 5** Installation type

         **Figure 5** Installation type

   f. Select **Custom (advanced)**.

      The **Where do you want to install Windows?** window is displayed.

      -  If the system displays a message indicating that no driver is found, go to :ref:`1.g <en-us_topic_0146474784__li2827143133314>`.


         .. figure:: /_static/images/en-us_image_0160277563.png
            :alt: **Figure 6** Installation path

            **Figure 6** Installation path

      -  If a disk is displayed, go to :ref:`1.j <en-us_topic_0146474784__li98272043173314>`.


         .. figure:: /_static/images/en-us_image_0160277966.png
            :alt: **Figure 7** Installation path

            **Figure 7** Installation path

   g. .. _en-us_topic_0146474784__li2827143133314:

      Click **Load Driver** and then **Browse**.


      .. figure:: /_static/images/en-us_image_0160277608.png
         :alt: **Figure 8** Loading drivers

         **Figure 8** Loading drivers

   h. Choose the following path and click **OK**.

      vmtools-windows/upgrade/$OS_Version/drivers/viostor

   i. Select the driver matching the OS and click **Next**.

      The system may provide multiple drivers. Select **VISOTOR.INF** shown in the following figure.


      .. figure:: /_static/images/en-us_image_0160277938.png
         :alt: **Figure 9** Selecting the driver to install

         **Figure 9** Selecting the driver to install

   j. .. _en-us_topic_0146474784__li98272043173314:

      Select the disk and click **Next**.


      .. figure:: /_static/images/en-us_image_0146478949.png
         :alt: **Figure 10** Installation path

         **Figure 10** Installation path

      .. note::

         If the disk type is **Offline**, you can stop and then start the ECS, and restart the OS installation process.


         .. figure:: /_static/images/en-us_image_0160826569.png
            :alt: **Figure 11** Offline disk

            **Figure 11** Offline disk

   k. The **Installing Windows** window is displayed, and the OS installation starts.

      The installation takes about 50 minutes. The ECS restarts during the installation. After the ECS successfully restarts, log in to it again and configure the OS as prompted.

      .. note::

         You are required to set a password for the OS user.

         Supported special characters include ``!@$%^-_=+[{}]:,./?``


      .. figure:: /_static/images/en-us_image_0146478951.png
         :alt: **Figure 12** Installation progress

         **Figure 12** Installation progress

#. Install related drivers.

   a. Open **Computer** and double-click the CD drive.


      .. figure:: /_static/images/en-us_image_0160277992.png
         :alt: **Figure 13** Starting the CD drive

         **Figure 13** Starting the CD drive

   b. Double-click the **vmtools-windows** folder.


      .. figure:: /_static/images/en-us_image_0160277998.png
         :alt: **Figure 14** Opening the **vmtools-windows** folder

         **Figure 14** Opening the **vmtools-windows** folder

   c. Double-click the **Setup** file.


      .. figure:: /_static/images/en-us_image_0160278257.png
         :alt: **Figure 15** Executing the Setup file

         **Figure 15** Executing the Setup file

   d. Install the driver as prompted.


      .. figure:: /_static/images/en-us_image_0160278288.png
         :alt: **Figure 16** Installing UVP VMTools for Windows

         **Figure 16** Installing UVP VMTools for Windows

   e. After the driver is installed, start **Device Manager** and verify that the drivers shown in the red box in the following figure are successfully installed.


      .. figure:: /_static/images/en-us_image_0160278272.png
         :alt: **Figure 17** Device Manager

         **Figure 17** Device Manager
