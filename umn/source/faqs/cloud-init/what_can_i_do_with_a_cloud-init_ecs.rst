:original_name: en-us_topic_0148873774.html

.. _en-us_topic_0148873774:

What Can I Do with a Cloud-Init ECS?
====================================

Introduction to Cloud-Init
--------------------------

Cloud-Init is an open-source tool for cloud instance initialization. When creating ECSs from an image with Cloud-Init, you can use user data injection to customize initialization details (for example, an ECS login password) to the ECSs. You can also configure and manage a running ECS by querying and using metadata. If Cloud-Init is not installed, you cannot apply these custom configurations to your ECSs, and you will have to use the original password in the image file to log in to the ECSs.

Installation Methods
--------------------

You are advised to install Cloud-Init or Cloudbase-Init on the ECS to be used to create a private image so that new ECSs created from this private image can be customized.

-  For Windows, download and install Cloudbase-Init.

   For details, see :ref:`Installing and Configuring Cloudbase-Init <en-us_topic_0030730602>`.

-  For Linux, download and install Cloud-Init.

   For how to install Cloud-Init, see :ref:`Installing Cloud-Init <en-us_topic_0030730603>`.

   For how to configure Cloud-Init, see :ref:`Configuring Cloud-Init <en-us_topic_0122876047>`.
