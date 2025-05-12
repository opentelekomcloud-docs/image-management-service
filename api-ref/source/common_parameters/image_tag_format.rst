:original_name: en-us_topic_0020092110.html

.. _en-us_topic_0020092110:

Image Tag Format
================

Description
-----------

You can attach a custom tag to a private image to facilitate private image management.

Format
------

Format of **tag**

-  The format is *key.value*. If a key is added, a tag is added. In other cases, the tag is updated.
-  The tag key can contain a maximum of 36 characters, and the tag value can contain a maximum of 43 characters. The tag value can be an empty character string.
-  The tag can contain only digits, letters, underscores (_), and hyphens (-).

Format of **image_tags**

-  The format is *{"key":"keyA", "value":"valueA"}*. If a key already exists when you add it, the tag will be updated.
-  The tag key can contain a maximum of 36 characters, and the tag value can contain a maximum of 43 characters. The tag value can be an empty character string.
-  If the first and last characters of the tag key and value are spaces, the system deletes the space by default.

Format (Native OpenStack)
-------------------------

Format of **tag**

-  The format is *key*. If a key is added, a tag is added. In other cases, the tag is updated.
-  The tag key can contain a maximum of 255 characters.
-  The tag can contain only digits, letters, underscores (_), and hyphens (-).
