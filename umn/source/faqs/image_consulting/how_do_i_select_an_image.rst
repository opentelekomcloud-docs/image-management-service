:original_name: en-us_topic_0195253327.html

.. _en-us_topic_0195253327:

How Do I Select an Image?
=========================

When creating an ECS or a BMS, you can select an image based on the following factors:

-  :ref:`Region and AZ <en-us_topic_0195253327__section79821850163918>`
-  :ref:`Image Type <en-us_topic_0195253327__section10191306168>`
-  :ref:`OS <en-us_topic_0195253327__section7760131584018>`

.. _en-us_topic_0195253327__section79821850163918:

Region and AZ
-------------

An image is a regional resource. You cannot use an image to create an instance in a different region. For example, when creating an instance in region A, you can only select an image that is already in region A. For more information, see :ref:`Region and AZ <en-us_topic_0171754221>`.

.. _en-us_topic_0195253327__section10191306168:

Image Type
----------

Images are classified into public images, private images, and shared images. A private image can be a system disk image, data disk image, or full-ECS image. For details, see :ref:`What Is Image Management Service? <en-us_topic_0013901609>`

.. _en-us_topic_0195253327__section7760131584018:

OS
--

When selecting an OS, consider the following factors:

-  Architecture types

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | System Architecture   | Applicable Memory     | Constraints                                                                                                                     |
   +=======================+=======================+=================================================================================================================================+
   | 32-bit                | Smaller than 4 GB     | -  If the instance memory is greater than 4 GB, a 32-bit OS cannot be used.                                                     |
   |                       |                       | -  A 32-bit OS only allows addressing within a 4 GB memory range. An OS with more than 4 GB memory cannot be accessed.          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | 64-bit                | 4 GB or larger        | If your application requires more than 4 GB of memory or the memory may need to be expanded to more than 4 GB, use a 64-bit OS. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+

-  OS types

   +-----------------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | OS Type               | Applicable Scenario                                                                                                | Constraints                                                                         |
   +=======================+====================================================================================================================+=====================================================================================+
   | Windows               | -  Programs developed for Windows (for example, .NET).                                                             | The system disk must be at least 1 GB, and there must be at least 1 GB of memory.   |
   |                       | -  Databases such as SQL Server. (You need to install the database.)                                               |                                                                                     |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | Linux                 | -  High-performance server applications (for example, Web) and common programming languages such as PHP and Python | The system disk must be at least 1 GB, and there must be at least 512 MB of memory. |
   |                       | -  Databases such as MySQL. (You need to install the database.)                                                    |                                                                                     |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
