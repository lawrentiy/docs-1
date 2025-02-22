# Questions about working with non-residents of Russia or Kazakhstan


#### Can I become a {{ yandex-cloud }} customer if I am a non-resident of Russia or Kazakhstan? {#non-resident}

Yes, but only if your legal status is a business.


#### Residents of what countries do you work with? {#countries}

Residents of the countries listed below can enter into an agreement and create a billing account.

{% include [non-resident-countries](../../billing/_includes/non-resident-countries.md) %}


#### Will you provide an agreement for the provision and payment of services? {#contract}

{% include [contract-qa](../../billing/_includes/contract-qa.md) %}

#### What payment methods can I use? {#payment-types}

Businesses that are non-residents of Russia or Kazakhstan and may top up their personal accounts and pay for consumed resources using a [bank card](../../billing/payment/payment-methods-card-business.md) or by [transferring funds from their bank account](../../billing/payment/payment-methods-business.md).


#### In what currency can non-residents of Russia or Kazakhstan pay for {{ yandex-cloud }} services? {#currency}

Non-residents of Russia or Kazakhstan can pay for {{ yandex-cloud }} services only in US dollars ($), whatever their country of residence.

#### What documents do I get after I pay for the services? {#documents}

{{ yandex-cloud }} generates a [payment invoice](../../billing/concepts/bill.md) for businesses that are non-residents of Russia or Kazakhstan. A copy of the payment invoice will be sent to the email address of the billing account owner at the beginning of the next reporting period.


#### How are taxes calculated when paying for services? {#taxes}

Taxes and fees of the country of registration of a non-resident business of Russia or Kazakhstan are not added to the cost of services on the [Usage details](../../billing/operations/check-charges.md) page, nor included into the total invoice amount.

Non-residents of Russia or Kazakhstan should pay all the taxes and fees themselves under the laws of their country of residence.

#### Why was my billing account created with the PAYMENT_NOT_CONFIRMED status? {#pending-status}

To activate a billing account for a non-resident of Russia or Kazakhstan, you must receive confirmation from {{ yandex-cloud }} managers.

When you click **{{ ui-key.yacloud.billing.accounts.button_empty-billing-create }}** on the **{{ ui-key.yacloud.billing.account.create-new.label_title }}** page, a billing account is created with the `PAYMENT_NOT_CONFIRMED` status. You will receive an email with further instructions to the email address specified in your Yandex or Yandex 360 account. It may take up to three business days to activate your account.

#### I received no email with instructions on what to do after creating a billing account. Why? {#account-notification}

It may take up to three business days to activate your billing account.
If no email arrived within that period, send a request to: [cloud_docs@support.yandex.ru](mailto:cloud_docs@support.yandex.ru).

In the request, specify the full organization name and the [billing account ID](../../billing/concepts/billing-account.md#billing-account-id), and attach a copy of the certificate of incorporation (translated into English or Russian).