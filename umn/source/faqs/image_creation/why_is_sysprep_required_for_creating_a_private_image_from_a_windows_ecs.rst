:original_name: en-us_topic_0030742197.html

.. _en-us_topic_0030742197:

Why Is Sysprep Required for Creating a Private Image from a Windows ECS?
========================================================================

Why Is Sysprep Required?
------------------------

For a user that needs to be added to a domain and uses the domain account to log in to Windows, Sysprep is required before a private image is created. Otherwise, the image will contain information about the original ECS, especially the SID. ECSs with the same SID cannot be added to a domain. If Windows does not require any user or ECS to be added to a domain, you do not need to run Sysprep.

.. caution::

   -  Before running Sysprep, ensure that Windows is activated.
   -  For details about Sysprep, visit https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-vista/cc721940(v=ws.10)?redirectedfrom=MSDN.

Restrictions on Running Sysprep
-------------------------------

Sysprep can only be used for configuring a new Windows installation. You can run Sysprep multiple times to install and configure Windows. However, you can reset and activate a Windows OS only three times, and you are not allowed to use Sysprep to re-configure an existing Windows OS.

.. note::

   In the Windows command line, enter the following command to check how many times you can run Sysprep in the displayed **Windows Script Host** dialog box:

   **slmgr /dlv**

   If the value of **Remaining Windows rearm count** is **0**, you cannot run Sysprep.
