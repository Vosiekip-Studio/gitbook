---
description: >-
  This page will walk us through installing a new release of your Tebex
  website without losing your settings.
---

# Updating

When we release a new version, you replace the website files and keep your own settings, uploads and add-ons. Your database is updated automatically.

Jump to the part that matches how you installed the website: [Hosting panel](#hosting-panel) or [VPS](#vps).

{% hint style="info" %}
Always make a backup first. If something goes wrong, you can go back to the old version.
{% endhint %}

***

## Hosting panel

No terminal needed.

{% stepper %}
{% step %}
### Backing up the database

1. Open **phpMyAdmin** in your panel.
2. Click your database (e.g. `USER_store`) on the left.
3. Press <mark style="color:$primary;">**Export**</mark>, then <mark style="color:$primary;">**Go**</mark>. Keep the downloaded file safe.
{% endstep %}

{% step %}
### Backing up your settings

1. In **File Manager**, turn on <mark style="color:$primary;">**Show hidden files**</mark> (in cPanel under **Settings**, top right).
2. Download these to your computer:
   * the file <kbd>tebex-store/.env</kbd>
   * the folder <kbd>tebex-store/storage</kbd>
   * the folder <kbd>tebex-store/theme/extras</kbd> (if you use add-ons)

{% hint style="warning" %}
The `.env` file holds your database password and Tebex keys. Keep it private.
{% endhint %}
{% endstep %}

{% step %}
### Replacing the files

1. Press <mark style="color:$primary;">**Stop**</mark> on the Node.js app page.
2. In **File Manager**, rename `tebex-store` to `tebex-store-old`.
3. Upload and extract the new <kbd>&lt;theme&gt;-store.tar.gz</kbd> into a fresh `tebex-store` folder, the same way as in [Uploading the files](hosting-panel-install.md).
4. Copy from `tebex-store-old` into the new `tebex-store`:
   * the `.env` file
   * the whole `storage` folder
   * the `theme/extras` folder, into `tebex-store/theme`
{% endstep %}

{% step %}
### Starting the new version

1. On the Node.js app page, press <mark style="color:$primary;">**Run NPM Install**</mark>, then <mark style="color:$primary;">**Start**</mark>, then <mark style="color:$primary;">**Restart**</mark>.
2. Sign in at `https://store.example.com/admin/login`. Any database updates run on this first page, and a banner tells you how many ran.
3. Open your store and check that everything works. Then delete `tebex-store-old`.
{% endstep %}
{% endstepper %}

***

## VPS

{% stepper %}
{% step %}
### Uploading the new release

Upload the new <kbd>&lt;theme&gt;-store.zip</kbd> to <kbd>/var/www/</kbd> with your SFTP client.
{% endstep %}

{% step %}
### Running the update

Log in to your server and run all of these commands:

{% hint style="warning" %}
**Change `<theme>` to the name of your theme** before you run these commands, it must match the file you uploaded.

Example: if your file is called `mytheme-store.zip`, then this line:

`unzip <theme>-store.zip -d tebex-store`

becomes:

`unzip mytheme-store.zip -d tebex-store`
{% endhint %}

```bash
mysqldump store > /root/store-backup-$(date +%F).sql
systemctl stop tebex-store
cd /var/www
rm -rf tebex-store-prev
mv tebex-store tebex-store-prev
unzip <theme>-store.zip -d tebex-store
rm <theme>-store.zip
cp -a tebex-store-prev/.env tebex-store-prev/storage tebex-store/
if [ -d tebex-store-prev/theme/extras ]; then cp -a tebex-store-prev/theme/extras tebex-store/theme/; fi
cd tebex-store
npm ci --omit=dev
node dist/cli.js migrate
chown -R www-data:www-data /var/www/tebex-store
systemctl start tebex-store
systemctl status tebex-store
```

The status must show **active (running)**. Press <mark style="color:$primary;">**q**</mark> to go back.

<details>

<summary>What do these commands do?</summary>

1. Back up your database to <kbd>/root/store-backup-DATE.sql</kbd>.
2. Stop the website.
3. Move the current version to <kbd>/var/www/tebex-store-prev</kbd> and unzip the new one.
4. Copy your `.env`, `storage` folder and add-ons into the new version.
5. Install packages, update the database and start the website again.

</details>
{% endstep %}

{% step %}
### Checking the website

Open your store and check that everything works.

{% hint style="info" %}
The previous version stays in <kbd>/var/www/tebex-store-prev</kbd>, in case you need to go back.
{% endhint %}
{% endstep %}
{% endstepper %}
