.. _OAuth2 Case Study:

####################################################
OAuth2 Case Study: Setting Up Microsoft Office 365 
####################################################

This section describes how to add and configure Microsoft Office 365
as an OAuth2 provider to an Open edX installation.

******************************
Obtain a Client ID and Secret
******************************

Microsoft Office 365 uses Microsoft Azure Active Directory as the directory and
OAuth2 provider for itself. So, in order to add Microsoft Office 365 as an
OAuth2 provider to your Open edX installation, you start with Microsoft Azure
Active Directory.

#. Obtain an Azure subscription. If you do not have one, you can create a free,
   short term trial subscription on the `Microsoft Azure`_ website. 

   .. note:: During setup,a credit card and phone number are required. If 
    you do not set up virtual machines or use paid services on the
    subscription, and only use it to access the Azure Active Directory, you
    will not be charged for the subscription.

#. To use Office 365 for third party authentication, you configure Microsoft
   Azure to manage your Office 365 Microsoft Azure Active Directory.

  #. Sign in to the `Azure portal`_.

  #. Either create a new Active Directory or select an existing one.
   
#. Register an application in Azure.

  #. Sign in to the Microsoft Azure Management Portal.

.. is this the same as the "Azure portal" in the previous step? 
.. Alison 22 Jul 2015

  #. Select the Active Directory icon from the left menu, and then select the
     Office 365 connected Azure active directory that you created or identified
     in the previous step.

  #. From the top menu select **Applications**, and then select **Add an App**.

  #. On the page that opens, select **Add an application my organization is
     developing**.

  #. On the Tell us about your application page, you specify a name for your
     application and indicate the type of application to register with Azure
     Active Directory. Select **web application**, **web API** (the default),
     or both, and then select the arrow icon at the bottom of the page.

  #. On the App properties page, enter the **Sign-on URL** for your Moodle
     instance. The Sign-on URL is the redirect URI for your Open edX
     installation. It must be entered with a trailing slash, for example, 
     ``https://example.com/auth/``.

.. is a Moodle instance a prerequisite? where is this info obtained?
.. Alison 22 Jul 2015

  #. Enter the **App ID URI** for your Moodle instance. This is the
     main URI of your Open edX installation.

  #. Select the checkbox at the bottom right of the page, and then select
     **Ok** to add your application to Azure Active Directory.

  #. There are a couple more values and changes you need to make and write down
     some values which you will need in the next section.

.. It isn't clear to me yet how this ^^ step and the "Configure the application" section below relate to each other. 
.. Alison 22 Jul 2015

#. Configure the application.

  #. Select the Active Directory icon from the left menu, and then select the
     Azure active directory you want to configure.

.. is this being done in the Azure portal? should they open a separate window so that info can be copied from one place in the portal to another?
.. Alison 22 Jul 2015

  #. Select the **Applications** tab.

  #. Select your application.

  #. Select **Configure**.

  #. Locate the client ID and copy it to the **Client ID** field in your OpenID
     connect configuration screen.

.. where do you locate this client ID? is it the client ID for the application you just created or located, and automatically assigned to the application? At what URL or application do you find the OpenID connect configuration screen? 
.. Alison 22 Jul 2015

  #. To create a client secret, locate the **keys** section and select a
     duration for the validity of the key. Save the new key, and then copy it
     to the **Client Secret** field in your OpenID connect configuration
     screen.

.. same question on the OpenID connect configuration screen
.. Alison 22 Jul 2015

#. OpenID Connect Settings.

.. is this also a configuration step? on the Azure portal still, or some other site?
.. Alison 22 Jul 2015 

  #. Locate the Permissions to other applications section.

  #. Select **Add application**. To do so, move the cursor over **Office 365
     Exchange Online and Office 365 SharePoint Online**, and then select the
     "plus sign" icon.

  #. Select the check mark icon at the bottom right of the dialog.

  #. In the Delegated Permissions dropdown for Windows Azure Active Directory,
     select the following permissions.

    * **Read directory data**

    * **Enable sign-on and read users' profiles**

  #. Select *Save*.

#. Add a user to the application.

  #. In the Azure portal, select the Active Directory icon from the left menu,
     and then select your Azure active directory.

  #. Select the **Applications** tab.

  #. Select your application.

  #. Select the **Users** tab.

  #. Select an Office 365 user to assign to the application.

  #. Select **Assign**.

  #. Select **Yes** to confirm the assignment.

=================================================================
Verify the Third Party Authentication Feature Setting
=================================================================

By default, third party authentication is not enabled on Open edX
installations. To enable it, you edit the ``lms.env.json`` file. For more
information, see :ref:`Enable the Third Party Authentication Feature`.

=================================================================
Add Azure Active Directory to the List of Approved Providers
=================================================================

To add Azure Active Directory to your whitelist, follow these steps.

#. Ensure that the ``azuread-oauth2`` backend class is accessible on your Open
   edX installation. If you have installed python-social-auth version 0.2.10 or
   later, you should already have the class.

#. Edit the ``lms.env.json`` file to add the backend class to
   "THIRD_PARTY_AUTH_BACKENDS".

=================================================================
Enabling and Configuring Azure Active Directory Provider
=================================================================

#. Log in to the Django administration console for your base URL. For example,
   ``http://{your_URL}/admin``.

#. In the **Third_Party_Auth** section, next to **Provider Configuration
   (OAuth2)** select **Add**.

#. For the **Icon class** select fa-sign-in, for **Name** enter Office 365, and
   then enter the **Client ID** and **Client Secret** that you obtained from
   the Azure portal.

   .. image:: ../../Images/add_office365_provider_config.png
     :alt: Screen shot of the Add provider configuration OAuth2 page with the
       specified settings for Office 365.

#. Specify other options, such as whether you want to treat the provider as
   primary or secondary, and whether you want to simplify the registration
   process by skipping the registration form or confirmation email.

#. Select **Enabled** to enable the provider.

#. Select **Save**.

At this point, if you go to the LMS login page, you should see the login button
for Office 365.

.. include:: ../../links.rst
