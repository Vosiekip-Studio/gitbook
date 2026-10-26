---
description: >-
  This page will walk us through everything you need before installing your
  Tebex website, and help you pick the right installation method.
---

# Installation guide

Unlike our Tebex themes, a Tebex website is a complete web application that runs on your own hosting and talks to Tebex in the background. That sounds more complicated than it is: we'll guide you through the entire process step by step, and nothing will be skipped, so you can follow along with confidence.

Before you start, read this page once from top to bottom. It tells you what you need and which of our two installation guides fits your hosting.

***

{% stepper %}
{% step %}
### Gather what you need

Make sure you have the following ready before you begin.

* **The website files** from your download: `accent-store.tar.gz` (hosting panel) or `accent-store.zip` (VPS).
* **A domain or subdomain** for your store, for example `store.example.com`.
* **Your Tebex API keys**: the <mark style="color:$primary;">**Public token**</mark> and the <mark style="color:$primary;">**Private key**</mark>.

<details>

<summary>Where to find your Tebex API keys</summary>

1. Open the [Tebex Creator Panel](https://creator.tebex.io/).
2. Go to <mark style="color:$primary;">**Store → Integrations → API Keys**</mark>.
3. Copy the **Public token** and the **Private key** and keep them somewhere safe, you will paste them in the setup wizard later.

{% hint style="warning" %}
Never share your **Private key** with anyone. It gives full access to your Tebex store.
{% endhint %}

</details>
{% endstep %}

{% step %}
### Check your hosting

The website needs a host that can run **Node.js** apps. A normal "PHP only" webhost (the kind used for WordPress) cannot run it.

Your hosting must have:

* **Node.js 22 or newer.** The website stops with an error on anything older.
* **MySQL 8** or **MariaDB 10.6** or newer.
* **Outbound HTTPS**, so the website can reach Tebex.
* **File Manager** or **SFTP**, so you can upload files.

{% hint style="info" %}
Not sure if your host has this? Send the list above to your hosting provider's support and ask if your plan supports it.
{% endhint %}
{% endstep %}

{% step %}
### Pick your installation method

Choose the guide that matches your hosting.

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Hosting panel install</strong></td><td>For shared or managed hosting with a control panel such as cPanel, Plesk, DirectAdmin or Webuzo. No commands needed for most steps.</td><td><a href="hosting-panel-install.md">hosting-panel-install.md</a></td></tr><tr><td><strong>VPS install</strong></td><td>For your own Ubuntu 22.04 or 24.04 server with root access. You will copy and paste a few commands.</td><td><a href="vps-install.md">vps-install.md</a></td></tr></tbody></table>

<details>

<summary>Which one should I pick?</summary>

* **You log in to a website with buttons and icons** (cPanel, Plesk, DirectAdmin, Webuzo) to manage your hosting → [Hosting panel install](hosting-panel-install.md).
* **You received an IP address and a root password** for a server → [VPS install](vps-install.md).

Other panels work too, as long as they have a **Node.js app manager** (a page where you can create a Node.js application).

</details>
{% endstep %}

{% step %}
### After the installation

Once your website is running, continue with these pages:

* [Add-ons](add-ons.md): install and set up extra pages such as the Rank Table, Vote Page and Gift Cards.
* [Updating](updating.md): install a new release without losing your settings.

After that, you can set up your webstore in Tebex the way you normally would for a Tebex theme.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Stuck somewhere? Don't hesitate to [reach out on Discord](https://discord.gg/PxwaKxKhb6), we're here to help.
{% endhint %}
