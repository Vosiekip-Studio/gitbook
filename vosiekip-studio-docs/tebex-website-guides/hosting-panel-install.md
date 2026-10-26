---
description: >-
  This page will walk us through installing your Tebex website on shared or
  managed hosting with a control panel, such as cPanel.
---

# Hosting panel install

This guide is for hosting with a control panel: cPanel, Plesk, DirectAdmin, Webuzo or any other panel with a **Node.js app manager**. In the examples we use **cPanel**, which is what our recommended host [Verpex](https://clients.verpex.com/aff/fdcfe91af7b811b092fe0ec8fb04ff84dddc52a8) uses. Other panels have the same options under slightly different names.

Haven't checked your hosting yet? Read the [installation guide →](installation-guide.md) first.

{% hint style="info" %}
**Replace these everywhere on this page:**

* `store.example.com` → your domain or subdomain
* `USER` → your hosting account username
* `CHANGE_THIS_PASSWORD` → a long password you make up for the database

The files you download start with the name of your theme. On this page we write that as `<theme>`, so `<theme>-store.zip` is your own theme's file.
{% endhint %}

***

{% stepper %}
{% step %}
### Uploading the files

First we upload the website files to your hosting account.

1. Open **File Manager** in your panel (or [connect with SFTP](connecting-with-sftp.md)).
2. Go to your home folder <kbd>/home/USER</kbd>.
3. Upload <kbd>&lt;theme&gt;-store.tar.gz</kbd> there.
4. Right-click the file, press <mark style="color:$primary;">**Extract**</mark>, and extract it to <kbd>/home/USER/tebex-store</kbd>.
5. Delete the <kbd>&lt;theme&gt;-store.tar.gz</kbd> file, you don't need it anymore.

You should now have a folder <kbd>/home/USER/tebex-store</kbd> with the folders `dist`, `theme`, `views`, `public` and the file `package.json` inside.

<!-- Screenshot: File Manager showing the extracted tebex-store folder -->

{% hint style="danger" %}
**Do not put this folder in `public_html`.** The website stores your database password, Tebex private key and encryption key in a `.env` file in this folder. Inside `public_html`, anyone could download that file.
{% endhint %}

<details>

<summary>Why the .tar.gz and not the .zip?</summary>

Many hosting panels scan uploads, and their scanner wrongly rejects any zip file that contains JavaScript. The `.tar.gz` file has the same content and passes the scan.

</details>
{% endstep %}

{% step %}
### Creating the Node.js app

Now we tell your panel to run the website.

Open the **Node.js** page in your panel. In cPanel this is <mark style="color:$primary;">**Software → Setup Node.js App**</mark>. Press <mark style="color:$primary;">**Create Application**</mark> and fill in:

| Setting                      | Value                                         |
| ---------------------------- | --------------------------------------------- |
| Node.js version              | `22` or higher                                |
| Application mode             | `Production`                                  |
| Application root             | `tebex-store`                                |
| Application URL              | `store.example.com`, leave the path **empty** |
| Application startup file     | `dist/server.js`                              |

Then add one **environment variable**:

| Name       | Value        |
| ---------- | ------------ |
| `NODE_ENV` | `production` |

Press <mark style="color:$primary;">**Create**</mark>. Leave the port alone, the panel takes care of it.

<!-- Screenshot: cPanel Setup Node.js App form filled in -->

{% hint style="warning" %}
The website must run on the root of a domain or subdomain. It will not work in a subfolder such as `store.example.com/shop`.
{% endhint %}
{% endstep %}

{% step %}
### Installing dependencies

The website needs some extra packages before it can start.

{% tabs %}
{% tab title="With the button" %}
1. On the app's page, press <mark style="color:$primary;">**Run NPM Install**</mark>.
2. Wait until it finishes.
3. Press <mark style="color:$primary;">**Restart**</mark>.
{% endtab %}

{% tab title="Without the button" %}
If your panel has no **Run NPM Install** button, we use the terminal instead.

1. Open **Terminal** in your panel (or connect with SSH).
2. At the top of the Node.js app's page, copy the command that starts with `source` and ends with `activate`. Paste it in the terminal and press **Enter**.
3. Run these commands:

```bash
cd ~/tebex-store
npm ci --omit=dev
```

4. When it finishes, press <mark style="color:$primary;">**Restart**</mark> on the app's page.
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Turning on SSL

SSL gives your store the padlock and the `https://` address. Do this **before** the setup wizard, because the wizard needs your `https://` address.

1. Open **SSL/TLS Status** in cPanel (or your panel's SSL page).
2. Issue a free **Let's Encrypt** certificate for `store.example.com`.
3. Turn on **Force HTTPS redirect** if your panel offers it.
{% endstep %}

{% step %}
### Creating the database

The website keeps its settings and data in a database.

1. Open **MySQL Databases** in your panel.
2. Create a database named `store`.
3. Create a user named `store` with your `CHANGE_THIS_PASSWORD`.
4. Add the user to the database and tick <mark style="color:$primary;">**All Privileges**</mark>.

{% hint style="warning" %}
**Write down the names exactly as the panel shows them.** Most panels put your account name in front, so `store` becomes `USER_store`. You need these exact names in the next step.
{% endhint %}

<!-- Screenshot: MySQL Databases page showing USER_store -->
{% endstep %}

{% step %}
### Getting your setup token

The setup wizard is protected with a one-time token, so nobody else can set up your store.

1. Open `https://store.example.com` in your browser. **It will show an error page, that is expected.** Opening it starts the website, which creates the token.
2. In **File Manager**, open <kbd>tebex-store/storage/setup-token.txt</kbd> and copy the token.
3. Open this address in your browser, with your token at the end:

{% code fullWidth="true" %}
```
https://store.example.com/install?token=PASTE_THE_TOKEN
```
{% endcode %}

<details>

<summary>The setup-token.txt file is not there</summary>

1. Press <mark style="color:$primary;">**Restart**</mark> on the Node.js app page.
2. Open `https://store.example.com` again.
3. Look in <kbd>tebex-store/storage</kbd> once more.

</details>
{% endstep %}

{% step %}
### Completing the setup wizard

Follow the wizard and fill in each screen as shown below.

{% tabs %}
{% tab title="1. Database" %}
1. **Environment checks:** press <mark style="color:$primary;">**Next: Database**</mark>.
2. Fill in:

| Field      | Value                                          |
| ---------- | ---------------------------------------------- |
| Host       | `localhost`                                    |
| Port       | `3306`                                         |
| Database   | the database name from step 5, e.g. `USER_store` |
| User       | the user name from step 5, e.g. `USER_store`     |
| Password   | your `CHANGE_THIS_PASSWORD`                    |
| Public URL | `https://store.example.com`                    |

3. Press <mark style="color:$primary;">**Test connection**</mark>, then <mark style="color:$primary;">**Save and run migrations**</mark>.
{% endtab %}

{% tab title="2. Owner account" %}
This is the account you use to log in to your store's admin panel.

1. Fill in **Name**, **Email**, **Password** and **Confirm password**. The password needs at least 12 characters.
2. Press <mark style="color:$primary;">**Create account**</mark>.
{% endtab %}

{% tab title="3. Tebex" %}
1. Paste your **Public token** and **Private key**.
2. Press <mark style="color:$primary;">**Test**</mark>, then <mark style="color:$primary;">**Save and continue**</mark>.
3. Press <mark style="color:$primary;">**Finish setup**</mark>.
{% endtab %}
{% endtabs %}

You can now sign in to your admin panel at `https://store.example.com/admin/login`.
{% endstep %}

{% step %}
### Connecting Tebex webhooks

Webhooks let Tebex tell your website when someone buys something. **This step is required**, without it purchases won't show up on your website.

1. In your store's admin panel, open <mark style="color:$primary;">**Settings → Integrations**</mark>.
2. In the Tebex Creator Panel, open **Webhooks** and copy the webhook **secret**.
3. Paste it into **Webhook secret** and press <mark style="color:$primary;">**Save changes**</mark>.
4. Click **Endpoint URL** to copy it.
5. In Tebex, add a new webhook endpoint and paste that URL.

<!-- Screenshot: Settings → Integrations in the admin panel -->
{% endstep %}
{% endstepper %}

***

🎉 **Your website is installed!** Continue with [setting up add-ons →](add-ons.md).

{% hint style="info" %}
**Where do I manage what?**

* **Your website's admin panel** (`https://store.example.com/admin/login`): theme settings, look and layout, and [add-ons](add-ons.md).
* **Tebex Creator Panel** ([creator.tebex.io](https://creator.tebex.io/)): packages and categories, payments and billing, and your wallet, just like before.
{% endhint %}
