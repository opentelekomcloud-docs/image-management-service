:original_name: en-us_topic_0106312064.html

.. _en-us_topic_0106312064:

How Do I Delete Redundant Network Connections from a Windows ECS?
=================================================================

Method 1
--------

#. Press **Win+R**. In the displayed dialog box, enter **regedit** and press **Enter** to open the registry editor.

#. Open the following registry key:

   **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\NetworkList\\Profiles**

   Click each item under **Profiles** and query the **Data** column of **ProfileName** in the right pane.

#. Double-click **ProfileName** and set **Value Data** to the name of a new network.

#. Restart the ECS for the change to take effect.

Method 2
--------

#. Press **Win+R**. In the displayed dialog box, enter **regedit** and press **Enter** to open the registry editor.

#. Open the following registry keys:

   **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\NetworkList\\Profiles**

   **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\NetworkList\\Signatures\\Unmanaged**

#. Delete the directories shown in the following figure.


   .. figure:: /_static/images/en-us_image_0207581512.png
      :alt: **Figure 1** Registry directory

      **Figure 1** Registry directory
