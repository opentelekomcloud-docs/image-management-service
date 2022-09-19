:original_name: en-us_topic_0113992021.html

.. _en-us_topic_0113992021:

What Do I Do If Injecting the Key or Password Using Cloud-Init Failed After NetworkManager Is Installed?
========================================================================================================

Symptom
-------

A major cause is that the version of Cloud-Init is incompatible with that of NetworkManager. In Debian 9.0 and later versions, NetworkManager is incompatible with Cloud-Init 0.7.9.

Solution
--------

Uninstall the current Cloud-Init and install Cloud-Init 0.7.6 or an earlier version.

For details about how to install Cloud-Init, see :ref:`Installing Cloud-Init <en-us_topic_0030730603>`.
