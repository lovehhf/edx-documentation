.. _Integrating with a SAML Identity Provider:

##########################################
Integrating with a SAML Identity Provider
##########################################

You can integrate your edX installation with federated identity solutions that
use the SAML 2.0 (Security Assertion Markup Language, version 2.0) standard. An
example is Shibboleth, a single sign on system that is used by many educational
institutions.

.. contents::
   :local:
   :depth: 1

*******************************************
Obtain and Set Up SAML Credentials
*******************************************

TBD 

.. what is happening here? is this a prereq to the rest of the procedures in this section, or independent of them? a sys admin does this once, are these credentials and identifying info for your site as a SAML service provider? where do you get or how do you generate the keys? I think this might be in the wrong place
.. Alison 23 July 2015

To configure your edX installation as a SAML service provider, follow
these steps.

#. Log in to the Django administration console for your base URL. For example,
   ``http://{your_URL}/admin``.

#. In the **Third_Party_Auth** section, next to **SAML Configuration** select
   **Add**.

#. Enter the following information.

  - **Private key**
  - **Public key**
  - **Entity ID**
  - **Organization Info**
  - **Other config str**

#. Select **Enabled** at the top of the page.

#. Select **Save** or one of the other save options at the bottom of the page.

**********************************************
Add an Identity Provider to your Configuration
**********************************************

To add a provider to your whitelist of approved identity providers, follow
these steps.

#. Ensure that the python-social-auth backend class for the provider that you
   want to use is accessible by your edX installation. For example, verify that
   the Django ``AUTHENTICATION_BACKENDS`` setting for the LMS contains
   ``third_party_auth.saml.SAMLAuthBackend``.

   If you are using the ``aws`` environment or a derived environment such as
   devstack, the ``lms/envs/aws.py`` script sets this class for you.

#. To customize the list of providers, edit the ``lms.env.json`` file to add
   the backend class to ``"THIRD_PARTY_AUTH_BACKENDS"``.

*******************************************
Add and Enable a SAML Provider
*******************************************

To add and enable a SAML 2.0 identity provider that is on your whitelist,
follow these steps.

#. Log in to the Django administration console for your base URL. For example,
   ``http://{your_URL}/admin``.

#. In the **Third_Party_Auth** section, next to **Provider Configuration
   (SAML IdPs)** select **Add**.

   To change the configuration of a provider, next to **Provider Configuration
   (SAML IdPs)** select **Change**, and then select the provider that you want
   to configure.

#. Enter the following information for the provider.

 - **Icon class**: Specifies the button style for users to select in order to
   access this IdP. For university or institutional providers, select **fa-
   university**.
 - **Name**: The name of the IdP as you want it to appear on the sign in page.
 - **Secondary**: Select this option to include the IdP in the list of
   providers that users access from the **fa-university**-styled button on the
   sign in page.
 - **Backend name**: Select the python-social-auth backend class for the
   provider. For example, **tpa-saml**.
 - **Idp slug**: A short, unique name to identify this IdP in the URL. The slug
   cannot include spaces.
 - **Entity ID**: The URI that identifies the IdP. This ID must match
   the value specified in the metadata XML file.
 - **Metadata source**: The URL of the XML file that contains this provider's
   metadata.

#. Specify your selections for other configuration options. For more
   information about these options, see :ref:`Configuration Options for SAML
   Providers`.

#. When you are ready to enable the provider, select **Enabled** at the top of
   the page. Alternatively, save your configuration settings and enable the
   provider at another time.

#. Select **Save** or one of the other save options at the bottom of the page.

.. _Configuration Options for SAML Providers:

*************************************************
Configuration Options for SAML Identity Providers
*************************************************

To customize the registration process for IdP, you make selections for these
optional fields on the Add Provider Configuration (SAML IdP) page.

* **Skip Registration Form**: If you select this option, users are not asked to
  confirm the user account data supplied for them by the IdP (name, email
  address, and so on). Select this option only for providers that are known to
  provide accurate user information.

  By default, users review a registration form with the supplied account
  details.

* **Skip Email Verification**: If you select this option, users are not
  required to confirm their email addresses, and their accounts are activated
  immediately upon registration.

  By default, users receive an email message and must select a link in that
  message to activate their user accounts.

* **User ID Attribute**: Required. This value is used to associate the user's
  edX account with the campus account. It is not displayed to users.

  By default, uses ``userid``, ``urn:oid:0.9.2342.19200300.100.1.1``.

* Optional user attributes: You can indicate specific SAML URNs attributes for
  the following user attributes. If you do not want an attribute to appear on
  the registration form, TBD.

  By default, the registration form includes all of the following attributes if
  they are provided by the IdP.

  * **Full Name Attribute**: ``commonName``, ``urn:oid:2.5.4.3``
  * **First Name Attribute**: ``givenName``, ``urn:oid:2.5.4.42``
  * **Last Name Attribute**: ``surname``, ``urn:oid:2.5.4.4``
  * **Username Hint Attribute**: ``userid``, 
    ``urn:oid:0.9.2342.19200300.100.1.1``
  * **Email Attribute**: ``mail``, ``urn:oid:0.9.2342.19200300.100.1.3``

.. Braden, how do you configure these so that they get left blank on the registration form? is there a special value that needs to be entered in these django admin fields? 
  
*******************************************
Test an Enabled SAML Provider
*******************************************

To verify the sign in process for an IdP that you have enabled, follow these
steps.

#. On the Django administration console, in the **Third_Party_Auth** section,
   select **Provider Configuration (SAML IdPs)**.

#. Check the icon in the **Metadata ready** column for the IdP. After the
   provider's metadata is fetched successfully from the URL that you provided
   as the metadata source, a check mark in a green circle appears and the
   provider is ready for use immediately.

   You might need to wait 30-60 seconds for the task to complete, and then
   refresh this page.
   
#. For additional information about the data fetched from the IdP, on the
   Django administration console select **SAML Provider Data**, and then select
   the provider. The page that opens reports data fetched from the metadata
   source URL and the date and time it was fetched.

#. To verify that users can use the IdP for sign in, go to the sign in page for
   your LMS. The page should include the institutional sign in button.

   .. image:: ../../Images/tpa_signin.png
     :alt: Screen shot of an LMS sign in page with a button labeled "Use my
         institutional/campus credentials" circled at the bottom.

#. Select **Use my institutional/campus credentials**. The list of providers
   that appears should include the IdP that you enabled.
   
   .. image:: ../../Images/tpa_inst_list.png
     :alt: Screen shot of the list of enabled IdPs. Each IdP name is linked to
         the sign in page for the corresponding authentication system.

