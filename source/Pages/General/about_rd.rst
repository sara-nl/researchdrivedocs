.. _about-rd:

.. image:: /Images/researchdrive3.png
           :width: 300px
           :align: right
           :target: https://researchdrive.surfsara.nl

********************
About Research Drive
********************

Research Drive is a service that allows researchers to store and share their research data with anyone in the world. Research Drive is based on the `Owncloud`_ software. The storage system used is SURFsara's `Object Store`_.

Research Drive can be accessed using the web interface at: https://researchdrive.surfsara.nl. It can be accessed using WebDAV, which enables you to use tools like Cyberduck, curl and others to access your data. WebDAV can also be used to couple Research Drive to other services supporting WebDAV.

Since Research Drive uses the `Owncloud`_ software, it can also be accessed with mobile clients for both Andoid and iOS and there is also a desktop client available for Windows, Mac OSX and Linux at `Owncloud's download page`_. 

Research Drive uses server-side encryption which means that the storage backend encrypts all data at rest and manages the encryption keys. Data transfers to and from Research Drive are encrypted using solely https.

.. note:: **Limitation:** Currently it is not possible to upload files larger than 5GB. We have reported this issue and Owncloud will fix this in the near future.

.. Links:

.. _`Owncloud`: https://owncloud.com
.. _`Object Store`: https://www.surf.nl/en/services-and-products/object-store/index.html
.. _`Owncloud's download page`: https://owncloud.com/download/
