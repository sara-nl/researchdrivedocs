.. _client_side_encryption:

.. image:: /Images/researchdrive3.png
           :width: 300px
           :align: right
           :target: https://researchdrive.surfsara.nl

**********************
Client-side encryption
**********************

.. image:: https://cryptomator.org/img/stage/logo.png
           :width: 150px
           :align: right
           :target: https:/cryptomator.org

Cryptomator
-----------

The Research Drive backend storage system is encrypted. But that is server-side encryption where the keys are managed by the storage system. If you want to manage the keys yourself and encrypt your files before uploading them there is a tool called `Cryptomator`_ that you can use. The Cryptomator software is available for Windows, Mac OSX and Linux. There are also mobile clients for iOS and Android.

Using Cryptomator you create an encrypted folder called a vault. In this vault you can put your data that will be encrypted. The encryption key will also reside in the vault but it is encrypted with a password. The vault can be unlocked by starting up the Cryptomator software and type in your password.

What you could do is to use Cryptomator together with Research Drive is to install the `Owncloud`_ sync client that syncs the contents of a folder in your computer to Research Drive. Then you can create a vault inside you sync folder. All data you put in your vault on your computer will be encrypted and then sent to Research Drive. 

If you want to share your encrypted data with someone, then you can share your vault using Research Drive. But you will need to get the password you have used to encrypt the key to the vault to the person you are sharing your data with. You have to do this in a secure manner like an encrypted email and this person needs to have Cryptomator installed.

The video below shows you how Cryptomator works together with Research Drive.

.. raw:: html

    <p style="text-align:center">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/XqFj7abvNqQ" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>
    </p>

.. Links:

.. _`Cryptomator`: https://cryptomator.org/
.. _`Owncloud`: https://owncloud.com/download/
