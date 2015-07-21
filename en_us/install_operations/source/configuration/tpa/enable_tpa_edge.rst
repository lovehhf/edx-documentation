
.. _Enabling Third Party Authentication:

##################################################
Enabling Third Party Authentication with edX Edge
##################################################

Partner institutions can enable third party authentication between their campus
or institutional authentication systems and the edX Edge site. Learners at
sites that enable third party authentication can use their campus credentials
to authenticate into edX Edge. This procedure requires collaboration between
the edX development operations team and members of the development operations
or IT teams at the partner institution.

.. future: add xref to section that describes complete open edX procedures
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

These steps should be performed by a member of your institution's IT team who
is familiar with your institutional Shibboleth system.

=======================================
Obtain edX Edge SAML Metadata
=======================================

The SAML metadata for Edge is available in an `XML file`_ on the Edge website.
The elements in this file provide values required to identify service providers
by your campus Shibboleth system.

============================================
Add edX Edge as a Service Provider
============================================

On your Shibboleth system, use the SAML metadata obtained from the XML file to
add edX Edge to your whitelist of allowed service providers.

For example, you might add the following information to your 
``$IDP_HOME/conf/relying-party.xml`` file. 

.. code:: xml

  <MetadataProvider xsi:type="FileBackedHTTPMetadataProvider" xmlns="urn:mace:shibboleth:2.0:metadata"
                    id="edxEdgeMetadata"
                    metadataURL="https://edge.edx.org/auth/saml/metadata.xml"
                    backingFile="/tmp/idp-metadata-edx-edge.xml" />

  
.. _Configure User Attributes:

=============================
Configure User Attributes
=============================

You work with the edX DevOps team to ensure that your provider asserts the user
information that you want learners to see during initial sign in on edX Edge.

Selecting User Attributes to Assert
************************************

By default, the edX platform uses these attributes if provided by your system.

* User identifier: ``userid``, ``urn:oid:0.9.2342.19200300.100.1.1``.
  Required. This value is used to associate the user's edX account with the
  campus account. It is not displayed to users.
* Full name: ``commonName``, ``urn:oid:2.5.4.3``
* First name: ``givenName``, ``urn:oid:2.5.4.42``
* Last name: ``surname``, ``urn:oid:2.5.4.4``
* Suggested username: ``userid``, ``urn:oid:0.9.2342.19200300.100.1.1``
* Email address: ``mail``, ``urn:oid:0.9.2342.19200300.100.1.3``

At your request, the edX DevOps team can configure Edge to use only some of
these attributes. The only required attribute is the user identifier. If you
choose not to provide other attributes, learners are prompted to enter that
information themselves during initial sign in.

Specifying Alternative Attributes
***********************************

You can work with the edX DevOps team to identify different attributes to
assert user information than those listed above. For example, you might send
the suggested username as ``eduPersonPrincipalName`` instead of ``userid``.

Restricting Access with Attribute Assertions
********************************************

You can restrict access to edX Edge to a subset of your users using attributes
defined on your Shibboleth system. For example, you might want to allow
currently matriculated students to sign in to Edge, but not alumni. The edX
DevOps team can restrict access by using the ``eduPersonEntitlement``
attribute. Be sure to let the edX DevOps team know what provider assertions to
use to determine access rights.

======================================================
Send Shibboleth Configuration Data to edX
======================================================

To complete the integration between your Shibboleth system and Edge, send
the following information to edX.

* Metadata: The URL for your Shibboleth metadata XML file. 

* Entity ID: The URI that identifies the Identity Provider. This ID must match
  the value specified in the metadata XML.

* User Attributes: A list of the values that you want your Shibboleth system to
  assert when users sign in to edX Edge. 

  For more information about how you can work with the edX DevOps team to
  configure user attributes effectively, see :ref:`Configure User
  Attributes`.


.. future: other SAML2-compliant identity providers
.. Alison 15 Jul 2015


.. _XML file: https://edge.edx.org/auth/saml/metadata.xml
