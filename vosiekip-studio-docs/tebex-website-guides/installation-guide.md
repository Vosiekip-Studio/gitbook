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

* **The website files** from your download: `<theme>-store.tar.gz` (hosting panel) or `<theme>-store.zip` (VPS). `<theme>` stands for the name of your theme.
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
### Choosing your hosting

Your website needs **hosting**: a computer on the internet that keeps your store online 24/7. The website runs on **Node.js**, so your hosting must support Node.js. Both kinds of hosting below work.

| Hosting | Web hosting <mark style="color:$success;">**(Recommended)**</mark> | VPS |
| --- | --- | --- |
| **What it is** | You share a server and manage everything through a website with buttons, such as **cPanel**. | You rent a whole server and control it by typing commands. |
| **Best for** | Beginners | People who are comfortable with a terminal |
| **Examples** | [Verpex](https://clients.verpex.com/aff/fdcfe91af7b811b092fe0ec8fb04ff84dddc52a8), or any host with cPanel, Plesk, DirectAdmin or Webuzo and Node.js support | [Hetzner](https://www.hetzner.com/cloud), [DigitalOcean](https://www.digitalocean.com/), [OVHcloud](https://www.ovhcloud.com/), [Verpex VPS](https://clients.verpex.com/aff/fdcfe91af7b811b092fe0ec8fb04ff84dddc52a8) |
| **Setup** | Mostly clicking, no commands needed | Copy and paste commands |
| **Guide** | [Hosting panel install](hosting-panel-install.md) | [VPS install](vps-install.md) |

{% hint style="success" %}
**Our recommendation: Verpex web hosting**

New to hosting? We recommend [Verpex](https://clients.verpex.com/aff/fdcfe91af7b811b092fe0ec8fb04ff84dddc52a8) web hosting. It comes with **cPanel**, **Node.js support**, databases and free SSL, it is very cheap, and our [Hosting panel install](hosting-panel-install.md) guide follows it step by step. The cheapest plan is enough for one store.
{% endhint %}

<details>

<summary>Already have hosting? Check these requirements</summary>

Your hosting must have:

* **Node.js 22 or newer.** The website stops with an error on anything older.
* **MySQL 8** or **MariaDB 10.6** or newer.
* **Outbound HTTPS**, so the website can reach Tebex.
* **File Manager** or **SFTP**, so you can upload files.

On a control panel, look for a **Node.js** page (in cPanel: **Software → Setup Node.js App**). If your panel doesn't have one, the website can't run there.

{% hint style="warning" %}
A "PHP only" webhost, the kind that only runs WordPress, cannot run the website. Not sure? Send the list above to your hosting provider's support and ask if your plan supports it.
{% endhint %}

</details>
{% endstep %}

{% step %}
### Pick your installation method

Choose the guide that matches the hosting you picked.

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Hosting panel install</strong> (recommended)</td><td>For web hosting with a control panel, such as Verpex with cPanel. No commands needed for most steps.</td><td><a href="hosting-panel-install.md">hosting-panel-install.md</a></td></tr><tr><td><strong>VPS install</strong></td><td>For your own Ubuntu 22.04 or 24.04 server with root access. You will copy and paste a few commands.</td><td><a href="vps-install.md">vps-install.md</a></td></tr></tbody></table>

<details>

<summary>Not sure which kind of hosting you have?</summary>

* **You log in to a website with buttons and icons** (cPanel, Plesk, DirectAdmin, Webuzo) to manage your hosting → [Hosting panel install](hosting-panel-install.md).
* **You received an IP address and a root password** for a server → [VPS install](vps-install.md).

</details>
{% endstep %}

{% step %}
### After the installation

Once your website is running, continue with these pages:

* [Add-ons](add-ons.md): install and set up extra pages such as the Rank Table, Vote Page and Gift Cards.
* [Updating](updating.md): install a new release without losing your settings.
* [Giving us access](giving-us-access.md): let our team help you safely with the installation.

Good to know: the **theme settings** and add-ons are managed in your website's own **admin panel**, not in Tebex anymore. Your **packages**, **payments**, **billing** and **wallet** are still managed in the [Tebex Creator Panel](https://creator.tebex.io/).
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Stuck somewhere? Don't hesitate to [reach out on Discord](https://discord.gg/PxwaKxKhb6), we're here to help.
{% endhint %}
