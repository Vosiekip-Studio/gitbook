---
description: >-
  This page will walk us through safely giving our team access to your hosting
  when we help you with the installation.
---

# Giving us access

Want us to install the website for you, or help when you're stuck? Then we need temporary access to your hosting. This page shows you how to do that safely, and how to take the access away again afterwards.

{% hint style="danger" %}
**Only share login details in a private Discord ticket.** Never post them in a public channel, and never share them with someone who messages you first. Our team will never ask for your Tebex Private key or payment details.
{% endhint %}

***

{% stepper %}
{% step %}
### Opening a ticket

1. Join our [Discord](https://discord.gg/PxwaKxKhb6).
2. Open a **support ticket** and tell us which hosting you use (for example Verpex) and what you need help with.
3. Wait for a team member to reply before you send any login details.
{% endstep %}

{% step %}
### Sharing your login

Pick the tab that matches your hosting.

{% tabs %}
{% tab title="Hosting panel (Verpex)" %}
Verpex and most other cPanel hosts don't have a "team member" or "invite" option. To set up the website we need your **cPanel login**, because the Node.js app and the database can only be made in cPanel.

1. Log in to your [Verpex Client Area](https://clients.verpex.com/).
2. Open your hosting plan and find your **cPanel username** and **password**. Forgot the password? Change it from the Client Area first.
3. Send us in your ticket:
   * your **domain**, for example `store.example.com`
   * your **cPanel username**
   * your **cPanel password**

{% hint style="warning" %}
Share your **cPanel** login only, **not** your Verpex Client Area login. The Client Area holds your billing and payment details, and we never need it.
{% endhint %}
{% endtab %}

{% tab title="VPS" %}
1. Send us in your ticket:
   * your server's **IP address**
   * the **root password**
   * your **domain**, for example `store.example.com`
2. If you already pointed your domain to the server, tell us. If not, we'll tell you what DNS record to add.

{% hint style="warning" %}
Share your server login only, **not** the login of your VPS provider's website. That account holds your billing and payment details, and we never need it.
{% endhint %}
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Removing our access afterwards

When we're done, change your password so the details you shared stop working.

{% tabs %}
{% tab title="Hosting panel (Verpex)" %}
1. Log in to your [Verpex Client Area](https://clients.verpex.com/).
2. Open your hosting plan and change your **cPanel password**.

This also changes the main FTP password. Your website keeps running, it doesn't use this password.
{% endtab %}

{% tab title="VPS" %}
1. Log in to your server (see [VPS install](vps-install.md)).
2. Run this command and type a new password twice:

```bash
passwd
```

You won't see the password while typing, that is normal. Your website keeps running, it doesn't use this password.
{% endtab %}
{% endtabs %}
{% endstep %}
{% endstepper %}
