---
title: Setting your billing email
intro: 'Your account''s billing email is where {% data variables.product.product_name %} sends receipts and other billing-related communication.'
redirect_from:
  - /github/setting-up-and-managing-billing-and-payments-on-github/setting-your-billing-email
  - /articles/setting-your-personal-account-s-billing-email
  - /articles/can-i-change-what-email-address-received-my-github-receipt
  - '/articles/how-do-i-change-the-billing-email,setting-your-billing-email'
  - /articles/setting-your-organization-s-billing-email
  - /articles/setting-your-billing-email
  - /github/setting-up-and-managing-billing-and-payments-on-github/managing-your-github-billing-settings/setting-your-billing-email
versions:
  fpt: '*'
  ghec: '*'
type: how_to
topics:
  - Organizations
  - User account
shortTitle: Billing email
---
## Setting your personal account's billing email

Your personal account's primary email is where {% data variables.product.product_name %} sends receipts and other billing-related communication.

Your primary email address is the first email listed in your account email settings.
We also use your primary email address as our billing email address.

If you'd like to change your billing email, see "[Changing your primary email address](/articles/changing-your-primary-email-address)."

## Setting your organization's billing email

Your organization's billing email is where {% data variables.product.product_name %} sends receipts and other billing-related communication. The email address does not need to be unique to the organization account.

{% data reusables.dotcom_billing.org-billing-perms %}

{% data reusables.organizations.billing-settings %}
1. Under "Billing management", to the right of the billing email address, click **Edit**.
  ![Current billing emails](/assets/images/help/billing/billing-change-email.png)
2. Type a valid email address, then click **Update**.
  ![Change billing email address modal](/assets/images/help/billing/billing-change-email-modal.png)

## Managing additional recipients for your organization's billing email

If you have users that want to receive billing reports, you can add their email addresses as billing email recipients. This feature is only available to organizations that are not managed by an enterprise.

{% data reusables.dotcom_billing.org-billing-perms %}

### Adding a recipient for billing notifications for your organization

{% data reusables.organizations.billing-settings %}
1. Under "Billing management", to the right of "Email recipients", click **Add**.
  ![Add recipient](/assets/images/help/billing/billing-add-email-recipient.png)
1. Type the email address of the recipient, then click **Add**.
  ![Add recipient modal](/assets/images/help/billing/billing-add-email-recipient-modal.png)

### Changing the primary recipient for billing notifications for your organization

One address must always be designated as the primary recipient. The address with this designation can't be removed until a new primary recipient is selected.

{% data reusables.organizations.billing-settings %}
1. Under "Billing management", find the email address you want to set as the primary recipient.
1. To the right of the email address, use the "Edit" drop-down menu, and click **Mark as primary**.
  ![Mark primary recipient](/assets/images/help/billing/billing-change-primary-email-recipient.png)

### Removing a recipient from billing notifications for your organization

{% data reusables.organizations.billing-settings %}
1. Under "Email recipients", find the email address you want to remove.
1. For the user's entry in the list, click **Edit**.
  ![Edit recipient](/assets/images/help/billing/billing-edit-email-recipient.png)
1. To the right of the email address, use the "Edit" drop-down menu, and click **Remove**.
  ![Remove recipient](/assets/images/help/billing/billing-remove-email-recipient.png)
1. Review the confirmation prompt, then click **Remove**.

{% ifversion ghec %}
## Setting your enterprise's billing email

Your enterprise's billing email is where {% data variables.product.product_name %} sends receipts and other billing-related communication. The email address does not need to be unique to the enterprise account.

Only enterprise members with the owner or billing manager role can access or change billing settings for your enterprise. For more information, see "[Managing users in your enterprise](/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise)."

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.billing-tab %}
1. Click **Billing emails**.
2. Under "Email recipients", to the right of the billing email address, click **Edit**.
  ![Screenshot of the current billing email with the edit button emphasized](/assets/images/help/billing/billing-change-email.png)
2. Type a valid email address, then click **Update**.
  ![Screenshot of the edit billing email address modal window with a sample email address entered](/assets/images/help/billing/billing-change-email-modal.png)

## Managing additional recipients for your enterprise's billing email

If you have users that want to receive billing reports, you can add their email addresses as billing email recipients.

Only enterprise members with the owner or billing manager role can access or change billing settings for your enterprise. For more information, see "[Managing users in your enterprise](/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise)."

### Adding a recipient for billing notifications for your enterprise

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.billing-tab %}
1. Click **Billing emails**.
2. Under "Email recipients", to the right of the billing email address, click **Add**.
   ![Screenshot of the current billing email with the add button emphasized](/assets/images/help/billing/billing-add-email-recipient.png)
3. Type the email address of the recipient, then click **Add**.
   ![Screenshot of the add billing email address modal window without a sample email address entered](/assets/images/help/billing/billing-add-email-recipient-modal.png)

### Removing a recipient from billing notifications for your enterprise

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.billing-tab %}
1. Click **Billing emails**.
2. Under "Email recipients", find the email address you want to remove.
3. For the user's entry in the list, click **Edit**.
   ![Screenshot of the recipient's email with the edit button emphasized](/assets/images/help/billing/billing-edit-email-recipient.png)
4. To the right of the email address, use the "Edit" drop-down menu, and click **Remove**.
   ![Screenshot of the recipient's email with the remove button emphasized](/assets/images/help/billing/billing-remove-email-recipient.png)
5. Review the confirmation prompt, then click **Remove**.
{% endif %}
