:original_name: en-us_topic_0046588154.html

.. _en-us_topic_0046588154:

Overview
========

IMS allows you to create encrypted images to ensure data security.

.. note::

   To use the image encryption function, you must apply for KMS Administrator permissions.

Constraints
-----------

-  KMS must be enabled.
-  Encrypted images cannot be shared with others.
-  The system disk of an ECS created from an encrypted image is also encrypted, and its key is the same as the image key.
-  If an ECS has an encrypted system disk, private images created from the ECS are also encrypted.
-  The key used for encrypting an image cannot be changed.
-  If the key used for encrypting an image is disabled or deleted, the image is unavailable.
