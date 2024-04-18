:original_name: en-us_topic_0146474781.html

.. _en-us_topic_0146474781:

Integrating the VMTools Driver into an ISO File
===============================================

Scenarios
---------

A Windows system with the Integrated Drive Electronics (IDE) hard drive and Virtio NIC is used on the cloud. Therefore, you need to integrate the VMTools driver into the ISO file of Windows before registering an image on the cloud platform. Typically, an ISO file contains all the files that would be included on an optical disc. Some software can be installed only from a CD-ROM drive. So, a virtual CD-ROM drive is required.

This section uses AnyBurn and UltraISO as examples to describe how to integrate the VMTools driver into an ISO file.

.. note::

   -  AnyBurn is lightweight CD/DVD/Blu-ray burning software with a free version.
   -  UltraISO is an ISO CD/DVD image file handling tool. A free trial version is limited to ISO files of 300 MB or less. You are advised to buy a standard version.

Prerequisites
-------------

You have obtained an ISO file.

.. note::

   The ISO file name can contain only letters, digits, hyphens (-), and underscores (_). If the name does not meet the requirements, change it.

AnyBurn
-------

#. Download `AnyBurn <http://www.anyburn.com/index.htm>`__ and install it on your local PC.

#. .. _en-us_topic_0146474781__li1056816092520:

   Download the VMTools driver package and decompress it to your local PC.

   For the mapping between Windows versions and VMTools packages, see :ref:`Obtaining Required Software Packages <en-us_topic_0037352059>`.

#. Use AnyBurn to open the ISO file.

   a. Open AnyBurn and select **Edit Image File**.

      |image1|

   b. Select the ISO file and click **Next**.

      |image2|

#. Edit the ISO file to integrate the VMTools driver into it.

   a. Decompress the **vmtools-windows.zip** file downloaded in :ref:`2 <en-us_topic_0146474781__li1056816092520>` to obtain **vmtools-windows.iso**, and then decompress **vmtools-windows.iso** to obtain the **vmtools-windows** folder.


      .. figure:: /_static/images/en-us_image_0000001492921309.png
         :alt: **Figure 1** **vmtools-windows** folder

         **Figure 1** **vmtools-windows** folder

   b. Drag and drop the **vmtools-windows** folder to the parent node of the ISO file (or click **Add** and select the folder to add it to the parent node), and click **Next**.

      |image3|

   c. Select a path to save the new ISO file and specify a name for the new file. Select **ISO** as the file type. Click **Create Now**.

      After the new ISO file is generated, view the VMTools driver in it.

      |image4|

UltraISO
--------

#. Download UltraISO and install it on your local PC.

   Download address: https://www.ultraiso.com/

#. .. _en-us_topic_0146474781__li7344112816270:

   Download the VMTools driver package and decompress it to your local PC.

   For the mapping between Windows versions and VMTools packages, see :ref:`Obtaining Required Software Packages <en-us_topic_0037352059>`.

#. Use UltraISO to open the ISO file.


   .. figure:: /_static/images/en-us_image_0179492273.png
      :alt: **Figure 2** Opening the ISO file

      **Figure 2** Opening the ISO file

   .. caution::

      Do not extract the ISO file or open it with some tool other than UltraISO, or the boot data will be lost.

#. .. _en-us_topic_0146474781__li159314251271:

   Decompress the **vmtools-windows.zip** file downloaded in :ref:`2 <en-us_topic_0146474781__li7344112816270>` to obtain **vmtools-windows.iso**, and then decompress **vmtools-windows.iso** to obtain the **vmtools-windows** folder.


   .. figure:: /_static/images/en-us_image_0179492194.png
      :alt: **Figure 3** **vmtools-windows** folder

      **Figure 3** **vmtools-windows** folder

#. Drag and drop the **vmtools-windows** folder obtained in :ref:`4 <en-us_topic_0146474781__li159314251271>` to the parent node of the ISO file.


   .. figure:: /_static/images/en-us_image_0185000270.gif
      :alt: **Figure 4** Adding the vmtools-windows folder to the ISO file

      **Figure 4** Adding the vmtools-windows folder to the ISO file

#. Use UltraISO to export the ISO file with the VMTools driver to an .iso file on your local PC.

.. |image1| image:: /_static/images/en-us_image_0000001493029617.png
.. |image2| image:: /_static/images/en-us_image_0000001443321198.png
.. |image3| image:: /_static/images/en-us_image_0000001493042877.png
.. |image4| image:: /_static/images/en-us_image_0000001493065701.png
