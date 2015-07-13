
.. _Enabling Third Party Authentication:

##################################################
Enabling Third Party Authentication with edX Edge
##################################################

Partner institutions can enable third party authentication between their campus
or institutional authentication systems and the edX Edge site. Learners at
sites that enable third party authentication can use their campus credentials
to authenticate into edX Edge. This procedure requires collaboration between
the edX development operations team and a member of the IT team at the partner
institution.

.. future: add xref to section describing complete open edX procedures
.. Alison 15 Jul 2015

.. contents::
   :local:
   :depth: 2

***********************************************
Integrating with Shibboleth (SAML) Systems
***********************************************

SAML 2.0 (Security Assertion Markup Language, version 2.0) is the standard that
edX uses for the exchange of authentication and authorization data with
institutional partners. Because it is built with SAML, this service
is compatible with the Shibboleth single sign on system.

In the exchange of authentication and authorization data, your edX partner
institution is an identity provider that securely asserts the identity and
access rights of a set of users. EdX is the service provider that allows the
users access on the basis of those credentials.

=======================================
Obtain edX Edge SAML Metadata
=======================================

This step can be performed by someone at your institution who has a user
account on edX Edge.

The SAML metadata for Edge is available in an `XML file`_ on the Edge website.
The elements in this file provide values required to identify service providers
by your campus Shibboleth system.

To access the XML file, you must log in to Edge. If no one at your institution
has a user account on Edge, contact the edX program manager who works with your
institution.

.. is this paragraph ^^ accurate?
.. Alison 15 Jul 2015

============================================
Add edX Edge as a Service Provider
============================================

This step should be performed by a member of your IT team who works with your
institutional Shibboleth system.

On your Shibboleth system, use the SAML metadata obtained from the XML file to
add edX Edge to the whitelist of allowed service providers.

.. I think that this means editing an XML file, but can't quite figure it out 
.. from a google search. Do we need more detail here or is this sufficient?
.. Alison 15 Jul 2015

======================================================
Send Shibboleth Configuration Data to edX
======================================================

This step should be performed by a member of your IT team who works with your
institutional Shibboleth system.

To complete the integration between your Shibboleth system and Edge, send
the following information to edX.

.. ^^ to whom and in what manner? email or JIRA story to devops? phone call to PM?

* Metadata: The URL for your Shibboleth metadata XML file. 

* Entity ID: The URL for 

* User Attributes: A list of the values that should be configured for assertion
  by your Shibboleth system on edX Edge. The attributes can include the
  following values.
  * Full name
  * First name
  * Last name
  * Hint (username)
  * Email address
  
.. Is this list complete? is it useful to have everything listed out like this?
.. should I explicitly say that they should let us know if they don't want to
.. assert anything?
.. Alison 15 Jul 2015


.. future: other SAML2-compliant identity providers
.. Alison 15 Jul 2015


.. _XML file: https://edge.edx.org/auth/saml/metadata.xml