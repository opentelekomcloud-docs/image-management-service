:original_name: en-us_topic_0125075471.html

.. _en-us_topic_0125075471:

Viewing the Virtualization Type of a Windows ECS
================================================

Open the cmd window and run the following command to query the virtualization type of the ECS:

**systeminfo**

If the values of **System Manufacturer** and **BIOS Version** are **Xen**, the ECS uses Xen. If KVM is required, perform the operations in this section to optimize a Windows private image.

.. note::

   If the ECS uses KVM, you are also advised to optimize the private image to prevent any exceptions with the ECSs created from the image.


.. figure:: /_static/images/en-us_image_0125154453.png
   :alt: **Figure 1** Viewing the virtualization type of a Windows ECS


   **Figure 1** Viewing the virtualization type of a Windows ECS
