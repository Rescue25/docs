---
title: Configuring SAML single sign-on for your enterprise
shortTitle: Configure SAML SSO
intro: 'You can control and secure access to {% ifversion ghec %}resources like repositories, issues, and pull requests within your enterprise''s organizations{% elsif ghes %}{% data variables.location.product_location %}{% elsif ghae %}your enterprise on {% data variables.product.prodname_ghe_managed %}{% endif %} by {% ifversion ghec %}enforcing{% elsif ghes or ghae %}configuring{% endif %} SAML single sign-on (SSO) through your identity provider (IdP).'
permissions: '{% ifversion ghes %}Site administrators{% elsif ghec or ghae %}Enterprise owners{% endif %} can configure SAML SSO for {% ifversion ghec or ghae %}an enterprise on {% data variables.product.product_name %}{% elsif ghes %}a {% data variables.product.product_name %} instance{% endif %}.'
versions:
  ghec: '*'
  ghes: '*'
  ghae: '*'
type: how_to
topics:
  - Accounts
  - Authentication
  - Enterprise
  - Identity
  - SSO
redirect_from:
  - /admin/authentication/configuring-saml-single-sign-on-for-your-enterprise
  - /github/setting-up-and-managing-your-enterprise/enabling-saml-single-sign-on-for-organizations-in-your-enterprise-account
  - /github/setting-up-and-managing-your-enterprise/configuring-identity-and-access-management-for-your-enterprise-account/enabling-saml-single-sign-on-for-organizations-in-your-enterprise-account
  - /github/setting-up-and-managing-your-enterprise/configuring-identity-and-access-management-for-your-enterprise-account/enforcing-saml-single-sign-on-for-organizations-in-your-enterprise-account
  - /admin/authentication/managing-identity-and-access-for-your-enterprise/configuring-saml-single-sign-on-for-your-enterprise
  - /admin/identity-and-access-management/managing-iam-for-your-enterprise/configuring-saml-single-sign-on-for-your-enterprise
---

{% data reusables.enterprise-accounts.emu-saml-note %}

## About SAML SSO

{% ifversion ghec %}

{% data reusables.saml.dotcom-saml-explanation %}

{% data reusables.saml.saml-accounts %}

For more information, see "[About identity and access management with SAML single sign-on](/organizations/managing-saml-single-sign-on-for-your-organization/about-identity-and-access-management-with-saml-single-sign-on)."

{% data reusables.saml.about-saml-enterprise-accounts %}

{% data reusables.saml.about-saml-access-enterprise-account %} For more information, see "[Viewing and managing a user's SAML access to your enterprise account](/admin/user-management/managing-users-in-your-enterprise/viewing-and-managing-a-users-saml-access-to-your-enterprise)."

{% data reusables.saml.saml-disabled-linked-identities-removed %}

{% data reusables.apps.reauthorize-apps-saml %}

{% elsif ghes or ghae %}

SAML SSO allows you to centrally control and secure access to {% data variables.location.product_location %} from your SAML IdP. When an unauthenticated user visits {% data variables.location.product_location %} in a browser, {% data variables.product.product_name %} will redirect the user to your SAML IdP to authenticate. After the user successfully authenticates with an account on the IdP, the IdP redirects the user back to {% data variables.location.product_location %}. {% data variables.product.product_name %} validates the response from your IdP, then grants access to the user.

After a user successfully authenticates on your IdP, the user's SAML session for {% data variables.location.product_location %} is active in the browser for 24 hours. After 24 hours, the user must authenticate again with your IdP.

{% data reusables.saml.saml-ghes-account-revocation %}

{% ifversion ghae %}

{% data reusables.saml.assert-the-administrator-attribute %}

{% data reusables.scim.after-you-configure-saml %} For more information, see "[Configuring user provisioning for your enterprise](/admin/authentication/configuring-user-provisioning-for-your-enterprise)."

{% endif %}

{% endif %}

## Supported identity providers

{% data reusables.saml.saml-supported-idps %}

{% ifversion ghec %}

## Username considerations with SAML

{% ifversion ghec %}If you use {% data variables.product.prodname_emus %}, {% endif %}{% data reusables.enterprise_user_management.consider-usernames-for-external-authentication %} For more information, see "[Username considerations for external authentication](/admin/identity-and-access-management/managing-iam-for-your-enterprise/username-considerations-for-external-authentication)."

## Enforcing SAML single-sign on for organizations in your enterprise account

When you enforce SAML SSO for your enterprise, the enterprise configuration will override any existing organization-level SAML configurations. {% data reusables.saml.switching-from-org-to-enterprise %} For more information, see "[Switching your SAML configuration from an organization to an enterprise account](/github/setting-up-and-managing-your-enterprise/configuring-identity-and-access-management-for-your-enterprise-account/switching-your-saml-configuration-from-an-organization-to-an-enterprise-account)."

When you enforce SAML SSO for an organization, {% data variables.product.company_short %} removes any members of the organization that have not authenticated successfully with your SAML IdP. When you require SAML SSO for your enterprise, {% data variables.product.company_short %} does not remove members of the enterprise that have not authenticated successfully with your SAML IdP. The next time a member accesses the enterprise's resources, the member must authenticate with your SAML IdP.

For more detailed information about how to enable SAML using Okta, see "[Configuring SAML single sign-on for your enterprise account using Okta](/admin/authentication/managing-identity-and-access-for-your-enterprise/configuring-saml-single-sign-on-for-your-enterprise-using-okta)."

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
1. {% data reusables.enterprise-accounts.view-current-policy-config-orgs %}
1. Under "SAML single sign-on", select **Require SAML authentication**.
1. In the **Sign on URL** field, type the HTTPS endpoint of your IdP for single sign-on requests. This value is available in your IdP configuration.
1. Optionally, in the **Issuer** field, type your SAML issuer URL to verify the authenticity of sent messages.
1. Under **Public Certificate**, paste a certificate to verify SAML responses.
{% data reusables.saml.edit-signature-and-digest-methods %}
1. Before enabling SAML SSO for your enterprise, click **Test SAML configuration** to ensure that the information you've entered is correct.
1. Click **Save**.
{% data reusables.enterprise-accounts.download-recovery-codes %}

{% elsif ghes %}

## Configuring SAML SSO

You can enable or disable SAML authentication for {% data variables.location.product_location %}, or you can edit an existing configuration. You can view and edit authentication settings for {% data variables.product.product_name %} in the {% data variables.enterprise.management_console %}. For more information, see "[Administering your instance from the {% data variables.enterprise.management_console %}](/admin/configuration/administering-your-instance-from-the-management-console)."

{% note %}

**Note**: {% data reusables.enterprise.test-in-staging %}

{% endnote %}

{% data reusables.enterprise_site_admin_settings.access-settings %}
{% data reusables.enterprise_site_admin_settings.management-console %}
{% data reusables.enterprise_management_console.authentication %}
1. Select **SAML**.

   ![Screenshot of option to enable SAML authentication in management console](/assets/images/enterprise/management-console/auth-select-saml.png)
1. {% data reusables.enterprise_user_management.built-in-authentication-option %}

   ![Screenshot of option to enable built-in authentication outside of SAML IdP](/assets/images/enterprise/management-console/saml-built-in-authentication.png)
1. Optionally, to enable unsolicited response SSO, select **IdP initiated SSO**. By default, {% data variables.product.prodname_ghe_server %} will reply to an unsolicited Identity Provider (IdP) initiated request with an `AuthnRequest` back to the IdP.

   ![Screenshot of option to enable IdP-initiated unsolicited response](/assets/images/enterprise/management-console/saml-idp-sso.png)

   {% tip %}

   **Note**: We recommend keeping this value **unselected**. You should enable this feature **only** in the rare instance that your SAML implementation does not support service provider initiated SSO, and when advised by {% data variables.contact.enterprise_support %}.

   {% endtip %}

1. Select **Disable administrator demotion/promotion** if you **do not** want your SAML provider to determine administrator rights for users on {% data variables.location.product_location %}.

   ![Screenshot of option to enable option to respect the "administrator" attribute from the IdP to enable or disable administrative rights](/assets/images/enterprise/management-console/disable-admin-demotion-promotion.png)
{%- ifversion ghes %}
1. Optionally, to allow {% data variables.location.product_location %} to receive encrypted assertions from your SAML IdP, select **Require encrypted assertions**.

   You must ensure that your IdP supports encrypted assertions and that the encryption and key transport methods in the management console match the values configured on your IdP. You must also provide {% data variables.location.product_location %}'s public certificate to your IdP. For more information, see "[Enabling encrypted assertions](/admin/identity-and-access-management/using-saml-for-enterprise-iam/enabling-encrypted-assertions)."
{%- endif %}
1. In the **Single sign-on URL** field, type the HTTP or HTTPS endpoint on your IdP for single sign-on requests. This value is provided by your IdP configuration. If the host is only available from your internal network, you may need to [configure {% data variables.location.product_location %} to use internal nameservers](/enterprise/admin/guides/installation/configuring-dns-nameservers/).

   ![Screenshot of text field for single sign-on URL](/assets/images/enterprise/management-console/saml-single-sign-url.png)
1. Optionally, in the **Issuer** field, type your SAML issuer's name. This verifies the authenticity of messages sent to {% data variables.location.product_location %}.

   ![Screenshot of text field for SAML issuer URL](/assets/images/enterprise/management-console/saml-issuer.png)
1. In the **Signature Method** and **Digest Method** drop-down menus, choose the hashing algorithm used by your SAML issuer to verify the integrity of the requests from {% data variables.location.product_location %}. Specify the format with the **Name Identifier Format** drop-down menu.

   ![Screenshot of drop-down menus to select signature and digest method](/assets/images/enterprise/management-console/saml-method.png)
1. Under **Verification certificate**, click **Choose File** and choose a certificate to validate SAML responses from the IdP.

   ![Screenshot of button for uploading validation certificate from IdP](/assets/images/enterprise/management-console/saml-verification-cert.png)
1. Modify the SAML attribute names to match your IdP if needed, or accept the default names.

   ![Screenshot of fields for entering additional SAML attributes](/assets/images/enterprise/management-console/saml-attributes.png)

{% elsif ghae %}

## Enabling SAML SSO

{% data reusables.saml.ae-enable-saml-sso-during-bootstrapping %}

The following IdPs provide documentation about configuring SAML SSO for {% data variables.product.product_name %}. If your IdP isn't listed, please contact your IdP to request support for {% data variables.product.product_name %}.

 | IdP | More information |
 | :- | :- |
 | Azure AD | "[Configuring authentication and provisioning for your enterprise using Azure AD](/admin/authentication/configuring-authentication-and-provisioning-with-your-identity-provider/configuring-authentication-and-provisioning-for-your-enterprise-using-azure-ad)" |
| Okta | "[Configuring authentication and provisioning for your enterprise using Okta](/admin/authentication/configuring-authentication-and-provisioning-with-your-identity-provider/configuring-authentication-and-provisioning-for-your-enterprise-using-okta)" |

During initialization for {% data variables.product.product_name %}, you must configure {% data variables.product.product_name %} as a SAML service provider (SP) on your IdP. You must enter several unique values on your IdP to configure {% data variables.product.product_name %} as a valid SP. For more information, see "[SAML configuration reference](/admin/identity-and-access-management/using-saml-for-enterprise-iam/saml-configuration-reference#saml-metadata)."

## Editing the SAML SSO configuration

If the details for your IdP change, you'll need to edit the SAML SSO configuration for {% data variables.location.product_location %}. For example, if the certificate for your IdP expires, you can edit the value for the public certificate.

{% ifversion ghae %}

{% note %}

**Note**: {% data reusables.saml.contact-support-if-your-idp-is-unavailable %}

{% endnote %}

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
1. Under "SAML single sign-on", type the new details for your IdP.
{% data reusables.saml.edit-signature-and-digest-methods %}
1. To ensure that the information you've entered is correct, click **Test SAML configuration**.
1. Click **Save**.
1. Optionally, to automatically provision and deprovision user accounts for {% data variables.location.product_location %}, reconfigure user provisioning with SCIM. For more information, see "[Configuring user provisioning for your enterprise](/admin/authentication/configuring-user-provisioning-for-your-enterprise)."

{% endif %}

{% ifversion ghae %}

## Disabling SAML SSO

{% warning %}

**Warning**: If you disable SAML SSO for {% data variables.location.product_location %}, users without existing SAML SSO sessions cannot sign into {% data variables.location.product_location %}. SAML SSO sessions on {% data variables.location.product_location %} end after 24 hours.

{% endwarning %}

{% note %}

**Note**: {% data reusables.saml.contact-support-if-your-idp-is-unavailable %}

{% endnote %}

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
1. Under "SAML single sign-on", deselect **Enable SAML authentication**.
1. To disable SAML SSO and require signing in with the built-in user account you created during initialization, click **Save**.

{% endif %}

{% endif %}

{% ifversion ghec or ghes %}

## Further reading

{%- ifversion ghec %}
- "[Managing SAML single sign-on for your organization](/organizations/managing-saml-single-sign-on-for-your-organization)"
{%- endif %}
{%- ifversion ghes %}
- "[Promoting or demoting a site administrator](/admin/user-management/managing-users-in-your-enterprise/promoting-or-demoting-a-site-administrator)"
{%- endif %}

{% endif %}
