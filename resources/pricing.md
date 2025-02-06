---
icon: square-dollar
---

# Pricing

Verida AI offers a flexible pricing model that allows you to manage API costs effectively while scaling your application. Below is an overview of how pricing works on our platform.

### Credits and API Requests

* **Credit Value:**\
  Each credit is valued at **0.01 USD**.
* **API Request Consumption:**
  * **Standard API Requests:** Most API requests consume **1 credit** per call.
  * **Intensive API Requests:** More resource-intensive operations (e.g., LLM processing or heavy searches) may consume **multiple credits**.

{% hint style="info" %}
_The exact number of credits consumed for each API endpoint is detailed in the respective API Documentation._
{% endhint %}

### Payment Options for API Requests

When your application requests access to user data, you have two payment options for covering API request costs:

1. **User-Paid Requests:**
   * The user authorizes and pays for the API requests initiated by your application.
2. **Developer-Paid Requests:**
   * Your application bears the cost for the API requests.

This flexibility ensures that you can choose the model that best suits your application's business logic and user experience.

{% hint style="info" %}
See [#generate-an-authentication-request-url](../getting-started/authentication.md#generate-an-authentication-request-url "mention")for more information on the `payer`attribute when authenticating with a user.
{% endhint %}

### Purchasing Additional Credits

If you need to increase your credit balance, you can purchase additional credits by acquiring Verida tokens (VDA) and converting them into credits directly through the [Developer Console](https://admin.verida.ai/).

* **Conversion Process:**
  1. **Purchase VDA:** Acquire Verida tokens from [supported exchanges](https://www.verida.network/vda-token).
  2. **Convert VDA to Credits:** Use the Developer Console to convert your VDA into credits.
*   **Dynamic Pricing with VDA:**\
    The conversion rate between VDA and credits is calculated dynamically at the time of each API request. This means that the amount of VDA deducted per API call reflects the current VDA price.

    **Examples:**

    * If **VDA is 0.01 USD** and your API call consumes **1 credit**, you will use **1 VDA**.
    * If **VDA is 0.10 USD** and your API call consumes **1 credit**, you will use **0.1 VDA**.

This dynamic pricing model ensures that the cost of API usage remains transparent and reflective of current market conditions.
