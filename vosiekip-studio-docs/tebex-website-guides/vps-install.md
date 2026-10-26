---
description: >-
  This page will walk us through installing your Tebex website on your own
  Ubuntu VPS.
---

# VPS install

This guide is for your own server running **Ubuntu 22.04 or 24.04**, logged in as `root`. You will copy and paste a few commands, we explain each part so you know what is happening.

Haven't checked your hosting yet? Read the [installation guide →](installation-guide.md) first.

{% hint style="info" %}
**Replace these everywhere on this page:**

* `YOUR_SERVER_IP` → your server's IP address
* `store.example.com` → your domain or subdomain
* `CHANGE_THIS_PASSWORD` → a long password you make up for the database

The files you download start with the name of your theme. On this page we write that as `<theme>`, so `<theme>-store.zip` is your own theme's file.
{% endhint %}

<details>

<summary>New to servers? Read this first</summary>

You need two kinds of programs on your own computer:

* **An SSH client** to type commands on your server. On Windows 10/11 and macOS you can use the built-in **Terminal**, or a program such as [PuTTY](https://www.putty.org/).
* **FileZilla** to upload files to your server. See [Connecting with SFTP](connecting-with-sftp.md) for how to install and use it.

**Copying and pasting commands:** copy a command from this page, paste it in your terminal and press **Enter**. In most terminals you paste with <mark style="color:$primary;">**Ctrl + Shift + V**</mark> or a right-click. Wait for each command to finish before running the next one.

</details>

***

{% stepper %}
{% step %}
### Pointing your domain to the server

Your domain needs to know where your server is.

1. Open your domain's **DNS settings** at your domain provider.
2. Add an **A record**:

| Field | Value                                   |
| ----- | --------------------------------------- |
| Name  | `@` for the main domain, or your subdomain (e.g. `store`) |
| Value | `YOUR_SERVER_IP`                        |

3. Save.

{% hint style="info" %}
DNS changes can take a while to spread, from a few minutes up to a few hours. You can continue with the next steps in the meantime, you only need the domain working at the **Turning on SSL** step.
{% endhint %}
{% endstep %}

{% step %}
### Logging in to the server

Open your terminal or SSH client and log in:

```bash
ssh root@YOUR_SERVER_IP
```

Type `yes` if it asks whether you trust the server, then enter your root password. You won't see the password while typing, that is normal.
{% endstep %}

{% step %}
### Installing the software

This installs everything the website needs: the web server (nginx), the database (MariaDB), SSL certificates (certbot) and Node.js 22.

```bash
apt update && apt upgrade -y
apt install -y curl unzip nginx mariadb-server certbot python3-certbot-nginx
curl -fsSL https://deb.nodesource.com/setup_22.x -o nodesource_setup.sh
bash nodesource_setup.sh
apt install -y nodejs
node -v
```

{% hint style="warning" %}
The last command must print **v22** or higher. If it shows a lower number, the website won't start.
{% endhint %}
{% endstep %}

{% step %}
### Creating the database

Open the database console:

```bash
mysql
```

Your terminal now shows `MariaDB [(none)]>`. Paste the lines below, after changing `CHANGE_THIS_PASSWORD` to your own password:

```sql
CREATE DATABASE store CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'store'@'localhost' IDENTIFIED BY 'CHANGE_THIS_PASSWORD';
GRANT ALL PRIVILEGES ON store.* TO 'store'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

This creates a database called `store` and a user called `store` with your password. `EXIT;` brings you back to the normal terminal.
{% endstep %}

{% step %}
### Uploading the website files

1. Open FileZilla and connect to `YOUR_SERVER_IP` as `root` (port `22`). New to FileZilla? Follow [Connecting with SFTP](connecting-with-sftp.md).
2. Upload <kbd>&lt;theme&gt;-store.zip</kbd> to the folder <kbd>/var/www/</kbd>.

<!-- Screenshot: FileZilla with the store zip in /var/www -->
{% endstep %}

{% step %}
### Unzipping and installing

Back in your terminal, run:

{% hint style="warning" %}
**Change `<theme>` to the name of your theme** before you run these commands, it must match the file you uploaded.

Example: if your file is called `mytheme-store.zip`, then this line:

`unzip <theme>-store.zip -d tebex-store`

becomes:

`unzip mytheme-store.zip -d tebex-store`
{% endhint %}

```bash
cd /var/www
unzip <theme>-store.zip -d tebex-store
rm <theme>-store.zip
cd tebex-store
npm ci --omit=dev
chown -R www-data:www-data /var/www/tebex-store
```

<details>

<summary>What do these commands do?</summary>

* `unzip` extracts the files to <kbd>/var/www/tebex-store</kbd>, then `rm` deletes the zip.
* `npm ci --omit=dev` installs the packages the website needs.
* `chown` gives the web server user (`www-data`) ownership of the files, so the website can run safely without root.

</details>
{% endstep %}

{% step %}
### Running the website as a service

A service keeps your website running in the background, and starts it again automatically after a crash or reboot.

Open a new file in the text editor `nano`:

```bash
nano /etc/systemd/system/tebex-store.service
```

Paste this into the editor:

{% code title="tebex-store.service" %}
```ini
[Unit]
Description=Tebex Store
After=network.target mariadb.service

[Service]
User=www-data
Group=www-data
WorkingDirectory=/var/www/tebex-store
Environment=NODE_ENV=production
Environment=HOST=127.0.0.1
Environment=PORT=3000
ExecStart=/usr/bin/node dist/server.js
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```
{% endcode %}

Save and close the editor: press <mark style="color:$primary;">**Ctrl + O**</mark>, then <mark style="color:$primary;">**Enter**</mark>, then <mark style="color:$primary;">**Ctrl + X**</mark>.

Now start the service:

```bash
systemctl daemon-reload
systemctl enable --now tebex-store
systemctl status tebex-store
```

The status must show **active (running)** in green. Press <mark style="color:$primary;">**q**</mark> to go back.

{% hint style="info" %}
**Already running another store on this server?** Use `PORT=3001` in the file above, and `127.0.0.1:3001` in the next step.
{% endhint %}
{% endstep %}

{% step %}
### Setting up nginx

nginx is the web server that sends visitors of your domain to the website.

Open a new file:

```bash
nano /etc/nginx/sites-available/tebex-store
```

Paste this, after changing `store.example.com` to your domain:

{% code title="tebex-store" %}
```nginx
server {
    listen 80;
    listen [::]:80;
    server_name store.example.com;
    client_max_body_size 8m;

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_read_timeout 60s;
    }
}
```
{% endcode %}

Save and close: <mark style="color:$primary;">**Ctrl + O**</mark>, <mark style="color:$primary;">**Enter**</mark>, <mark style="color:$primary;">**Ctrl + X**</mark>. Then turn the site on:

```bash
ln -s /etc/nginx/sites-available/tebex-store /etc/nginx/sites-enabled/
rm -f /etc/nginx/sites-enabled/default
nginx -t
systemctl reload nginx
```

`nginx -t` must say **test is successful**. If it shows an error, open the file again and check that you pasted everything.
{% endstep %}

{% step %}
### Opening the firewall

This only allows SSH (so you can log in) and web traffic to your server:

```bash
ufw allow OpenSSH
ufw allow 'Nginx Full'
ufw enable
```

Press <mark style="color:$primary;">**y**</mark> and **Enter** when it asks to continue.
{% endstep %}

{% step %}
### Turning on SSL

SSL gives your store the padlock and the `https://` address. Run this, after changing `store.example.com` to your domain:

```bash
certbot --nginx -d store.example.com
```

1. Enter your email.
2. Agree to the terms.
3. If it asks about redirecting, choose **redirect**.

{% hint style="warning" %}
This only works once your domain points to the server (step 1). If certbot fails, wait a bit for DNS and try again.
{% endhint %}
{% endstep %}

{% step %}
### Getting your setup token

The setup wizard is protected with a one-time token, so nobody else can set up your store. Show it with:

```bash
cat /var/www/tebex-store/storage/setup-token.txt
```

Select the token it prints and copy it. Then open this address in your browser, with your token at the end:

{% code fullWidth="true" %}
```
https://store.example.com/install?token=PASTE_THE_TOKEN
```
{% endcode %}
{% endstep %}

{% step %}
### Completing the setup wizard

Follow the wizard and fill in each screen as shown below.

{% tabs %}
{% tab title="1. Database" %}
1. **Environment checks:** press <mark style="color:$primary;">**Next: Database**</mark>.
2. Fill in:

| Field      | Value                       |
| ---------- | --------------------------- |
| Host       | `127.0.0.1`                 |
| Port       | `3306`                      |
| Database   | `store`                    |
| User       | `store`                    |
| Password   | your `CHANGE_THIS_PASSWORD` |
| Public URL | `https://store.example.com` |

3. Press <mark style="color:$primary;">**Test connection**</mark>, then <mark style="color:$primary;">**Save and run migrations**</mark>.
{% endtab %}

{% tab title="2. Owner account" %}
This is the account you use to log in to your store's admin panel.

1. Fill in **Name**, **Email**, **Password** and **Confirm password**.
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

**Your website's admin panel** (`https://store.example.com/admin/login`):

* **Settings:** store name, logo, favicon, Tebex integration and SEO.
* **Theme:** store texts, footer, social media, sale, announcement, realm selector, colors and custom CSS.
* **Add-ons:** set up your installed [add-ons](add-ons.md).
* **Modules:** the panels in the store's sidebar, such as a payment goal or community goal.
* **Content:** translations, images and uploads.
* **System:** sync with Tebex, activity log and your account.

**Tebex Creator Panel** ([creator.tebex.io](https://creator.tebex.io/)): packages and categories, pages, payments and billing, and your wallet, just like before.

Changed something in Tebex? It shows on your website within a few minutes. To see it right away, press **System → Sync now** in the admin panel.
{% endhint %}
