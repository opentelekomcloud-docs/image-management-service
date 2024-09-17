:original_name: en-us_topic_0030742197.html

.. _en-us_topic_0030742197:

Why Is Sysprep Required for Creating a Private Image from a Windows ECS?
========================================================================

Why Is Sysprep Required?
------------------------

`Sysprep <https://technet.microsoft.com/zh-cn/library/cc721940(v=ws.10).aspx>`__ is used to generalize images. It removes server-specific information, like the security identifier (SID), from an image so that ECSs created from this image can have unique SIDs in a domain. If your windows ECSs do not need to join a domain, Sysprep is not required.

.. caution::

   Before running Sysprep, ensure that Windows is activated.

Restrictions on Running Sysprep
-------------------------------

Sysprep can only be used to configure new installations of Windows and not to reconfigure an existing installation. You can run Sysprep as many times as required to build and to configure your installation of Windows. However, you can reset Windows activation only up to three times.

.. note::

   In the Windows command line, run the following command to check how many times you can run Sysprep:

   **slmgr /dlv**

   In the displayed **Windows Script Host** dialog box, if the value of **Remaining Windows rearm count** is **0**, you cannot run Sysprep.
