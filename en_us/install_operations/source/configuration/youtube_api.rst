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

The Open edX Platform uses `Version 3 of the YouTube API`_, which requires that
the application uses an API key.

To get the YouTube API key, follow YouTube's `instructions for obtaining
authorization credentials`_.

.. Note::  
  Before proceeding, review :ref:`Guidelines for Updating the edX Platform`.

.. _Version 3 of the YouTube API: https://developers.google.com/youtube/v3/
.. _instructions for obtaining authorization credentials: https://developers.google.com/youtube/registering_an_application

*************************************************************************
Set the YouTube API Key in the Open edX Platform
*************************************************************************

#. Set the value of ``YOUTUBE_API_KEY`` in the ``/cms/envs/common.py`` and
   ``/lms/envs/common.py`` files to the key you obtained from YouTube.
   
   .. code-block:: bash

       YOUTUBE_API_KEY = 'YOUR_YOUTUBE_API_KEY'

#. Save the the ``/cms/envs/common.py`` and ``/lms/envs/common.py`` files.
