.. _Integrating with an OAuth2 Identity Provider:

#############################################
Integrating with an OAuth2 Identity Provider
#############################################

You can integrate your edX installation with federated identity solutions that
use the OAuth2 standard. An example is Microsoft Office 365 with Microsoft
Azure Active Directory.

.. contents::
   :local:
   :depth: 1

*****************************************************************
Obtain a Client ID and Secret from the OAuth2 Provider
*****************************************************************

Before you can add an OAuth2 identity provider to your edX installation, you
must register your edX installation with that site as a service provider. You
visit the identity provider's site to obtain a client ID and secret for your
installation. All OAuth2 providers have well defined interfaces for this
process.

*****************************************************************
Add an OAuth2 Identity Provider to your Configuration
*****************************************************************

To add a provider to your whitelist of approved identity providers, follow
these steps.

#. Ensure that the python-social-auth backend class for the provider that you
   want to use is accessible by your edX installation. 

   If you are using the ``aws`` environment or a derived environment such as
   devstack, the ``lms/envs/aws.py`` script sets this class for you.

#. To customize the list of providers, edit the ``lms.env.json`` file to add
   the backend class to ``"THIRD_PARTY_AUTH_BACKENDS"``.


*************************************************
Add and Enable an OAuth2 Provider
*************************************************

To add and enable an OAuth2 identity provider that is on your whitelist, follow
these steps.

#. Log in to the Django administration console for your base URL. For example,
   ``http://{your_URL}/admin``.

#. In the **Third_Party_Auth** section, next to **Provider Configuration
   (OAuth2)** select **Add**.

   To change the configuration of a provider, next to **Provider Configuration
   (OAuth2)** select **Change**, and then select the provider that you want to
   configure.

#. Enter the following information for the provider.

 - **Icon class**: Specifies the button style for users to select in order to
   access this IdP. 
 - **Name**: The name of the of the IdP as you want it to appear on the sign in
   page.
 - **Backend name**: Select the python-social-auth backend class for the
   provider. For example, **azuread-oauth2**.

#. Specify your selections for other configuration options. For more
   information about these options, see :ref:`Configuration Options for OAuth2
   Providers`.

#. When you are ready to enable the provider, select **Enabled** at the top of
   the page. Alternatively, save your configuration settings and enable the
   provider at another time.

#. Select **Save** or one of the other save options at the bottom of the page.

.. _Configuration Options for OAuth2 Providers:


*************************************************
Configuration Options for OAuth2 Providers
*************************************************
 
To customize the registration process for an IdP, you make selections for these
optional fields on the Add Provider Configuration (OAuth2) page.

- **Secondary**: Select this option to include the IdP in the list of
   providers that users access from the icon class button on the
   sign in page.

  The list of providers enabled for an edX installation can be divided into two
  categories: Primary and Secondary. Providers from the primary list are
  displayed prominently on the login / registration pages (with a button).
  Secondary providers are displayed less prominently, in a separate list of
  "Institution" login providers.

  Here is an example of the signin page for primary providers.

  TBD 

  Here is an example of the signin page for secondary providers. 

  TBD 

* **Skip Registration Form**: 

  In order to make the registration process simpler, edX makes it possible to
  simply absorb the user's details (such as name, email etc.) silently from
  their OAuth2 provider instead of asking them to confirm them. This option
  should be used only for trusted providers that are known to provide accurate
  user information.

* **Skip Email Verification**: 

  At the end of the registration process, edX sends an email to the email
  address provided during registration to confirm the identity of the user. For
  trusted providers, the admin can choose to skip this part so users will not
  be required to confirm their email, and their account will be activated
  immediately upon registration.

* **Client ID**
* **Client Secret**
* **Other settings**
 

************************************************************************
Specify default third party authentication via QueryString parameter
************************************************************************

If the link to a course includes a query parameter (tpa_hint) that specifies
one of the enabled third party authentication providers, and the user is not
logged in to that provider, the third party authentication sign in flow with
the specified provider will be automatically started instead of redirecting the
user to the login page.


*********************************
Test an Enabled OAuth2 Provider
*********************************

To verify the sign in process for an IdP that you have enabled, follow these
steps.

TBD 
 
#. To verify that users can use the IdP for sign in, go to the sign in page for
   your LMS. The page should include the selected sign in button.

   .. image:: TBD
     :alt: Screen shot of an LMS sign in page with a button labeled "TBD"
         circled at the bottom.

#. Select **TBD**. The list of providers
   that appears should include the IdP that you enabled.
   
   .. image:: TBD
     :alt: Screen shot of the list of enabled IdPs. Each IdP name is linked to
         the sign in page for the corresponding authentication system.
