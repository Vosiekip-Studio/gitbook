---
description: >-
  This page will walk us through registering a domain with Namecheap and
  pointing it to your hosting or server.
---

# Setting up your domain

Your store needs its own address, such as `mystore.com` or `store.mynetwork.com`. That address is called a **domain**. In this guide we register one at [Namecheap](https://www.namecheap.com/) and point it to your hosting with an **A record**.

{% hint style="info" %}
**Already own a domain?** Skip to [Finding your IP address](#finding-your-ip-address). Your domain doesn't have to be at Namecheap, every domain provider has the same DNS settings under slightly different names.
{% endhint %}

<details>

<summary>Domain or subdomain, what's the difference?</summary>

* **Domain:** `mynetwork.com`. You buy this once a year.
* **Subdomain:** `store.mynetwork.com`. A free extra address on a domain you already own. Great if your network's website already runs on `mynetwork.com`.

Both work for your store. Pick a subdomain if you already have a domain for your network, so you don't have to buy a new one.

</details>

***

{% stepper %}
{% step %}
### Registering your domain

1. Go to [namecheap.com](https://www.namecheap.com/) and type the name you want in the search bar, for example `mynetwork`.
2. Pick an available domain from the list, `.com` and `.net` are the most common. Press <mark style="color:$primary;">**Add to cart**</mark>.
3. Press <mark style="color:$primary;">**Checkout**</mark>. Leave **Domain Privacy** on, it hides your name and address from the public, and it's free.
4. Create a Namecheap account and complete the payment.

{% hint style="warning" %}
Check the **renewal price** before you buy. Some domains are very cheap for the first year and much more expensive after that.
{% endhint %}
{% endstep %}

{% step %}
### Finding your IP address

The A record sends visitors of your domain to your hosting. For that you need your hosting's **IP address**, a number like `123.45.67.89`.

{% tabs %}
{% tab title="Hosting panel (cPanel)" %}
1. Log in to **cPanel**.
2. Look at the **General Information** box on the right side of the page.
3. Copy the number next to <mark style="color:$primary;">**Shared IP Address**</mark>.

Can't find it? Your hosting's welcome email usually lists it too, or ask your host's support.
{% endtab %}

{% tab title="VPS" %}
Your server's IP address is in the welcome email from your VPS provider, and in their dashboard next to your server.
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Adding the A record

1. Log in to Namecheap and open <mark style="color:$primary;">**Domain List**</mark> in the menu on the left.
2. Press <mark style="color:$primary;">**Manage**</mark> next to your domain.
3. Open the <mark style="color:$primary;">**Advanced DNS**</mark> tab.
4. Under **Host Records**, press <mark style="color:$primary;">**Add New Record**</mark> and choose **A Record**.
5. Fill in:

| Field | What to fill in |
| ----- | --------------- |
| Host  | `@` for the domain itself (`mynetwork.com`), or the first part of your subdomain, e.g. `store` for `store.mynetwork.com` |
| Value | your IP address from the previous step |
| TTL   | `Automatic` |

6. Press the green ✔ to save.

<!-- Screenshot: Namecheap Advanced DNS with the A record filled in -->

<details>

<summary>I don't see Host Records</summary>

Your domain uses other nameservers. Open the **Domain** tab, set **Nameservers** to <mark style="color:$primary;">**Namecheap BasicDNS**</mark>, press the green ✔, and go back to **Advanced DNS**.

</details>

<details>

<summary>There is already an A record for @ or www</summary>

Namecheap adds a "parking page" record to new domains. If you use the domain itself (`@`) for your store, delete the existing `@` record and the `www` **CNAME Record** that points to `parkingpage.namecheap.com`, then add your own.

</details>
{% endstep %}

{% step %}
### Adding the domain to your hosting

This step is only for **hosting panels**. On a **VPS** you can skip it, nginx takes care of it in the [VPS install](vps-install.md).

Your hosting must also know the domain, otherwise it won't show up in the **Application URL** list when you create the Node.js app.

* **Is it the main domain** you chose when ordering your hosting? Then it's already added, you can skip this step.
* **Is it a different domain or a subdomain?** Add it in cPanel:

1. Open <mark style="color:$primary;">**Domains → Domains**</mark> in cPanel and press <mark style="color:$primary;">**Create A New Domain**</mark>.
2. Type your domain or subdomain, for example `store.mynetwork.com`.
3. Untick **Share document root**, then press <mark style="color:$primary;">**Submit**</mark>.
{% endstep %}

{% step %}
### Waiting for DNS

DNS changes take a while to spread across the internet, usually a few minutes and sometimes up to a few hours.

You can check it at [dnschecker.org](https://dnschecker.org/): type your domain, pick **A**, and press **Search**. When most locations show a green tick and your IP address, your domain is ready.

{% hint style="info" %}
You can continue with the installation in the meantime. You only need the domain working when you **turn on SSL**.
{% endhint %}
{% endstep %}
{% endstepper %}

***

Domain ready? Continue with your installation guide: [Hosting panel install](hosting-panel-install.md) or [VPS install](vps-install.md).
