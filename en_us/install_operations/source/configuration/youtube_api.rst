.. include:: ../links.rst

.. _YouTube_API:

####################
Set YouTube API Key
####################

This section describes how to set the YouTube API key for your instance of
Open edX.

.. contents::
   :local:
   :depth: 1

*********
Overview
*********

If you intend for courses on your Open edX instance to include videos that are
hosted on YouTube, you must get a YouTube API key and set the key in the
Open edX Platform.

The Open edX Platform uses the `YouTube Data API v3`_, which requires that
the application uses an API key.

*************************
Getting a YouTube API key
*************************

To get the YouTube API key, follow YouTube's `instructions for obtaining
authorization credentials`_.

.. Note::
  Before proceeding, review :ref:`Guidelines for Updating the edX Platform`.

.. _YouTube Data API v3: https://developers.google.com/youtube/v3/
.. _instructions for obtaining authorization credentials: https://developers.google.com/youtube/registering_an_application

******************************************
Installing the YouTube API key in Open edX
******************************************

Once you've gotten a YouTube API key, you'll need put that key into your
Open edX installation. There are two different ways you can do this.

Option 1: Ansible (recommended)
===============================

`Ansible`_ is the automation system used for installing and updating Open edX.
If you set your YouTube API key in Ansible's configuration file, then Ansible
will make sure that the YouTube API key remains in place as you update Open
edX.

To set your YouTube API key in Ansible's configuration file, follow these
instructions:

#. Find the `configuration`_ repository on your Open edX server. If you are
   running devstack or fullstack, this will be
   ``/edx/app/edx_ansible/edx_ansible``.

#. In that repository, open the ``playbooks/roles/edxapp/defaults/main.yml``
   file in a text editor.

#. Find the line that looks like this:
   ``EDXAPP_YOUTUBE_API_KEY: "PUT_YOUR_API_KEY_HERE"``
   Replace ``PUT_YOUR_API_KEY_HERE`` with your YouTube API key. Make sure
   that your YouTube API key is still surrounded by quotation marks when
   you are done.

#. Save the file in your text editor, and close it.

#. Run Ansible so that it applies your YouTube API key to your Open edX
   installation. If you are running the Cypress named release, you can run:

   .. code-block:: bash

      /edx/bin/update edx-platform named-release/cypress

.. _configuration: https://github.com/edx/configuration

Option 2: JSON files
====================

Ansible outputs information to several JSON files used by Open edX. If you'd
prefer not to edit Ansible configuration, you can edit these files directly.
However, every time you update Open edX, your edits will be overwritten by
Ansible. As a result, we recommend setting your YouTube API key in Ansible's
configuration instead.

To set your YouTube API key by editing JSON files, follow these instructions:

#. Find the `edx-platform`_ repository on your Open edX server. If you are
   running devstack or fullstack, this will be ``/edx/app/edxapp/edx-platform``.

#. In the directory *above* your repository, there should be several JSON files,
   including ``lms.auth.json`` and ``cms.auth.json``. If you are running devstack
   or fullstack, this will be in the ``/edx/app/edxapp`` directory.

#. Open the ``lms.auth.json`` file in your text editor. Find the line that
   looks like this:
   ``"YOUTUBE_API_KEY": "PUT_YOUR_API_KEY_HERE",``
   Replace ``PUT_YOUR_API_KEY_HERE`` with your YouTube API key. Make sure
   that your YouTube API key is still surrounded by quotation marks when
   you are done.

#. Save the file in your text editor, and close it.

#. Open the ``cms.auth.json`` file and make the same change. If that line does
   not exist in this file, create it.

#. Save the file in your text editor, and close it.

.. _edx-platform: https://github.com/edx/edx-platform
