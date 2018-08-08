.. _rclone:

******
rclone
******

In this page you will find documentation about rclone. Rclone is the rsync for cloud storage. Information on how to install rclone and other things may be found at: https://rclone.org. 

Apart from being an rsync-type tool for cloud storage, it has the following features:

* MD5/SHA1 hashes checked at all times for file integrity
* Timestamps preserved on files
* Partial syncs supported on a whole file basis
* `Copy <https://rclone.org/commands/rclone_copy/>`_ mode to just copy new/changed files
* `Sync <https://rclone.org/commands/rclone_sync/>`_ (one way) mode to make a directory identical
* `Check <https://rclone.org/commands/rclone_check/>`_ mode to check for file hash equality
* Can sync to and from network, eg two different cloud accounts
* Optional encryption ( `Crypt <https://rclone.org/crypt/>`_ )
* Optional FUSE mount ( `rclone mount <https://rclone.org/commands/rclone_mount/>`_ )

.. contents:: 
    :depth: 4

=============
Authorisation
=============

Rclone needs some variables set in order to work. You can set these in a **rclone.conf** file. This file can have the following contents:

.. code-block:: console

    [RD]
    type = webdav
    url = https://researchdrive.surfsara.nl/remote.php/webdav/
    vendor = owncloud
    user = <user name>
    pass = <encrypted password>

This file can be generated interactively with the following command:

.. code-block:: console

    rclone config

Then you get the following options:

.. image:: /Images/rcloneconfig.png

1. Select **n** for new remote and choose the name, RD in this example
2. Select the storage system. Select **Webdav**
3. Fill in the URL. In this case this will be: **https://researchdrive.surfsara.nl/remote.php/webdav**
4. Select the type of webdav storage system. Select **Owncloud**
5. Type in your user name.
6. Select: **y) Yes type in my own password**
7. Type in your password and type it in again for confirmation. This is the webdav password you have in the ResearchDrive web page at Settings->Security->WebDAV passwords
8. Confirm your settings

The **rclone.conf** file resides in **.config/rclone/** by default.

If you want to put the **rclone.conf** file in a non-standard place, then that is possible too, but then you need to run your rclone commands in the following manner:

.. code-block:: console

    rclone --config /path/to/rclone.conf <command> .......

==============================================
Copy source directory to destination directory
==============================================

.. code-block:: console

    rclone copy /my/folder RD:my/destination/folder

Copy the source to the destination. Doesn’t transfer unchanged files, testing by size and modification time or MD5SUM. Doesn’t delete files from the destination.

If **my/destination/folder** doesn’t exist, it is created and the contents of **/my/folder** goes there.

==========================
Working with large objects
==========================

When you want to upload large files to ResearchDrive, we recommend using a timeout of 10 minutes per gigabyte of the largest source file. As an example, the largest file in the source directory is 5GB. Calculating the argument for --timeout gives: 10 minutes x 5GB = 50 minutes.

.. code-block:: console
    rclone -v copy --timeout 50m ~/my_5gb_file.bin RD:my/destination/folder

================================================
Sync source directory with destination directory
================================================

.. code-block:: console

    rclone sync /my/folder RD:my/destination/folder

Sync the source to the destination, changing the destination only. Doesn’t transfer unchanged files, testing by size and modification time or MD5SUM. Destination is updated to match source, including deleting files if necessary.


.. note:: **Important:** Since this can cause data loss, test first with the --dry-run flag to see exactly what would be copied and deleted.

Note that files in the destination won’t be deleted if there were any errors at any point.

If **my/destination/folder** doesn’t exist, it is created and the contents of **/my/folder** goes there.

==================================================
Check if files in the source and destination match
==================================================

.. code-block:: console

    rclone check /my/folder RD:my/destination/folder

Checks the files in the source and destination match. It compares sizes and hashes (MD5 or SHA1) and logs a report of files which don’t match. It doesn’t alter the source or destination.

==============================================
Use rclone to mount file systems in user space
==============================================

Using rclone to mount a file system in user space is done as follows:

.. code-block:: console

    rclone mount RD:[path/to/dir] /path/to/local/mount

You can unmount this file system by:

.. code-block:: console

     fusermount -u /path/to/local/mount

An example is shown below:

.. image:: /Images/rclonemount.png
