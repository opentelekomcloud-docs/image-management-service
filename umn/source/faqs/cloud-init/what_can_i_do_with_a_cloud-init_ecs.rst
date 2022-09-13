:original_name: en-us_topic_0148873774.html

.. _en-us_topic_0148873774:

What Can I Do with a Cloud-Init ECS?
====================================

Introduction to Cloud-Init
--------------------------

Cloud-Init is an open-source tool for cloud instance initialization. When creating ECSs from an image with Cloud-Init, you can use user data injection to inject customized initialization details (for example, an ECS login password) to the ECSs. You can also configure and manage a running ECS by querying and using metadata. If Cloud-Init is not installed, you cannot apply custom configurations to the ECSs. You will have to use the original password in the image file to log in to the ECSs.

Installation Methods
--------------------

You are advised to install Cloud-Init or Cloudbase-Init on the ECS to be used to create a private image so that new ECSs created from the private image support custom configurations.

-  For Windows OSs, download and install Cloudbase-Init.

   For how to install Cloudbase-Init, see :ref:`Installing and Configuring Cloudbase-Init <en-us_topic_0030730602>`.

-  For Linux OSs, download and install Cloud-Init.

   For how to install Cloud-Init, see :ref:`Installing Cloud-Init <en-us_topic_0030730603>`.

   For how to configure Cloud-Init, see :ref:`Configuring Cloud-Init <en-us_topic_0122876047>`.
