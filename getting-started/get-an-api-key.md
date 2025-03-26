---
description: Learn how to obtain a Verida API key to access user data
icon: lock-a
---

# Get an API key

There are currently three ways to obtain an API key to use the Verida APIs:

1. Generate your own key with the Verida Vault
2. Generate your own key with the Developer console
3. Request a key from a user of your application

{% hint style="info" %}
Note: To generate your own key, you will need to first Install the [Verida Wallet](https://www.verida.network/verida-wallet) mobile application to create your own self-custody account to store your data and connect some data sources to your account with the [verida-vault.md](../resources/verida-vault.md "mention").
{% endhint %}

## Generate your own key with the Verida Vault

You can generate your own private API key from the [verida-vault.md](../resources/verida-vault.md "mention") ([https://app.verida.ai/](https://app.verida.ai/)), in the `Authorized Apps` menu item.

<figure><img src="../.gitbook/assets/Screenshot 2025-03-25 at 3.40.56 PM.png" alt=""><figcaption><p>Click "Authorized Apps" to generate a personal API token.</p></figcaption></figure>

## Generate your own key with the Developer Console

You can generate your own private API key from the [developer-console.md](developer-console.md "mention") ([https://admin.verida.ai/](https://admin.verida.ai/)), in the `Generate Token` menu item.

<figure><img src="../.gitbook/assets/Screenshot 2025-03-25 at 3.44.49 PM.png" alt=""><figcaption><p>Click "Generate Token" to request a token from the Verida Vault with your Verida account.</p></figcaption></figure>

## Request a key from a user of your application

If you are building an application, you can request a key directly from the user by embedding a `Connect Verida` button into your application with pre-configured scopes to request.

See the [developer-console.md](developer-console.md "mention") and [authentication.md](authentication.md "mention") sections of the documentation to learn more.
