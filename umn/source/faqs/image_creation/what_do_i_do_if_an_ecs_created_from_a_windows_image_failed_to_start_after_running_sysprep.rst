:original_name: en-us_topic_0030713206.html

.. _en-us_topic_0030713206:

What Do I Do If an ECS Created from a Windows Image Failed to Start After Running Sysprep?
==========================================================================================

Symptom
-------

#. After Sysprep is executed, the following message is displayed when you start the ECS.


   .. figure:: /_static/images/en-us_image_0130934915.png
      :alt: **Figure 1** Message displayed

      **Figure 1** Message displayed

   Then, the following information is displayed in the dialog box:

   .. code-block:: text

      Windows could not parse or process the unattend answer file for pass [specialize]. A component or setting specified in the answer file does not exist. The error was detected while processing settings for component [Microsoft-Windows-Shell-Setup].

#. Click **OK**. The following information is displayed in the dialog box:

   .. code-block:: text

      The computer accidentally restarts or encounters an error. Windows installation cannot continue. Click OK to restart the computer and restart the installation.

#. Open **setupact.log** in **C:\\Windows\\Panther**. The log contains the following information.


   .. figure:: /_static/images/en-us_image_0207384171.jpg
      :alt: **Figure 2** Viewing ECS logs

      **Figure 2** Viewing ECS logs

Solution
--------

#. Create an ECS from a public image. (You are advised to use a public image to create another ECS because Sysprep can be executed only for certain times.)
#. Create an **Unattend.xml** file or modify the **Unattend.xml** file provided by the system.

   -  If you create an **Unattend.xml** file, ensure that the created file is used when you run Sysprep. For details about the file, visit:

      -  https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/update-windows-settings-and-scripts-create-your-own-answer-file-sxs
      -  https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/sysprep--system-preparation--overview

   -  If you modify the **Unattend.xml** file (in the **C:\\Program Files\\Cloudbase Solutions\\Cloudbase-Init\\conf** directory), delete the **RunSynchronous** part from the file.


      .. figure:: /_static/images/en-us_image_0130522831.png
         :alt: **Figure 3** Deleting the RunSynchronous part

         **Figure 3** Deleting the RunSynchronous part

#. Run Sysprep. For details, see :ref:`Running Sysprep <en-us_topic_0093887081>`.

   .. important::

      If you use the **Unattend.xml** file created by yourself, check the **Unattend.xml** path when running Sysprep to ensure that the newly created **Unattend.xml** file is used.

#. Create an image from the ECS where Sysprep has been executed.
