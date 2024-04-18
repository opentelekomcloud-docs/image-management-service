:original_name: en-us_topic_0030713141.html

.. _en-us_topic_0030713141:

Product Advantages
==================

IMS provides convenient, secure, flexible, and efficient image management. Images allow you to deploy services faster, more easily and more securely.

Saving Time and Effort
----------------------

-  Deploying services on cloud servers is much faster and easier when you use images.
-  A private image can be created from an ECS or an external image file. It can be a system, disk, or full-ECS image that suites your different needs.
-  Private images can be transferred between accounts, regions, or cloud platforms through image sharing, replication, and export.

Secure
------

-  Public images use mainstream OSs such as Ubuntu and CentOS. These OSs have been thoroughly tested to provide secure and stable services.
-  Multiple copies of image files are stored on Object Storage Service (OBS), which provides excellent data reliability and durability.
-  Private images can be encrypted for data security by using envelope encryption provided by Key Management Service (KMS).

Flexible
--------

-  You can manage images through the management console or using APIs.
-  You can use a public image to deploy a general-purpose environment, or use a private image to deploy a custom environment.
-  You can use IMS to migrate servers to the cloud or on the cloud, and back up server running environments.

Unified
-------

-  IMS provides a self-service platform to simplify image management and maintenance.
-  IMS allows you to batch deploy and upgrade application systems, improving O&M efficiency and ensuring consistency.
-  Public images comply with industry standards. Preinstalled components only include clean installs, and only kernels from well-known third-party vendors are used to make it easier to transfer images from or to other cloud platforms.

Comparison Between Image-based Deployment and Manual Deployment
---------------------------------------------------------------

.. table:: **Table 1** Image-based deployment and manual deployment

   +---------------+---------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Item          | Image-based Deployment                                                                                                                      | Manual Deployment                                                                                                                        |
   +===============+=============================================================================================================================================+==========================================================================================================================================+
   | Time required | 2 to 5 minutes                                                                                                                              | 1 to 2 days                                                                                                                              |
   +---------------+---------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Complexity    | Quickly create ECSs by using public images or private images.                                                                               | Select an appropriate OS, database, and various software packages based on your service requirements. Then, install and commission them. |
   +---------------+---------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Security      | You only need to identify sources of shared images. Public and private images have been thoroughly tested to ensure security and stability. | The security depends on the skills of the R&D or O&M personnel.                                                                          |
   +---------------+---------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
