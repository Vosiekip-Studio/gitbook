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
2. Click your database (e.g. `USER_accent`) on the left.
3. Press <mark style="color:$primary;">**Export**</mark>, then <mark style="color:$primary;">**Go**</mark>. Keep the downloaded file safe.
{% endstep %}

{% step %}
### Backing up your settings

1. In **File Manager**, turn on <mark style="color:$primary;">**Show hidden files**</mark> (in cPanel under **Settings**, top right).
2. Download these to your computer:
   * the file <kbd>accent-store/.env</kbd>
   * the folder <kbd>accent-store/storage</kbd>
   * the folder <kbd>accent-store/theme/extras</kbd> (if you use add-ons)

{% hint style="warning" %}
The `.env` file holds your database password and Tebex keys. Keep it private.
{% endhint %}
{% endstep %}

{% step %}
### Replacing the files

1. Press <mark style="color:$primary;">**Stop**</mark> on the Node.js app page.
2. In **File Manager**, rename `accent-store` to `accent-store-old`.
3. Upload and extract the new <kbd>accent-store.tar.gz</kbd> into a fresh `accent-store` folder, the same way as in [Uploading the files](hosting-panel-install.md).
4. Copy from `accent-store-old` into the new `accent-store`:
   * the `.env` file
   * the whole `storage` folder
   * the `theme/extras` folder, into `accent-store/theme`
{% endstep %}

{% step %}
### Starting the new version

1. On the Node.js app page, press <mark style="color:$primary;">**Run NPM Install**</mark>, then <mark style="color:$primary;">**Start**</mark>, then <mark style="color:$primary;">**Restart**</mark>.
2. Sign in at `https://store.example.com/admin/login`. Any database updates run on this first page, and a banner tells you how many ran.
3. Open your store and check that everything works. Then delete `accent-store-old`.
{% endstep %}
{% endstepper %}

***

## VPS

{% stepper %}
{% step %}
### Uploading the new release

Upload the new <kbd>accent-store.zip</kbd> to <kbd>/var/www/</kbd> with your SFTP client.
{% endstep %}

{% step %}
### Running the update

Log in to your server and run all of these commands:

```bash
mysqldump accent > /root/accent-backup-$(date +%F).sql
systemctl stop accent-store
cd /var/www
rm -rf accent-store-prev
mv accent-store accent-store-prev
unzip accent-store.zip -d accent-store
rm accent-store.zip
cp -a accent-store-prev/.env accent-store-prev/storage accent-store/
if [ -d accent-store-prev/theme/extras ]; then cp -a accent-store-prev/theme/extras accent-store/theme/; fi
cd accent-store
npm ci --omit=dev
node dist/cli.js migrate
chown -R www-data:www-data /var/www/accent-store
systemctl start accent-store
systemctl status accent-store
```

The status must show **active (running)**. Press <mark style="color:$primary;">**q**</mark> to go back.

<details>

<summary>What do these commands do?</summary>

1. Back up your database to <kbd>/root/accent-backup-DATE.sql</kbd>.
2. Stop the website.
3. Move the current version to <kbd>/var/www/accent-store-prev</kbd> and unzip the new one.
4. Copy your `.env`, `storage` folder and add-ons into the new version.
5. Install packages, update the database and start the website again.

</details>
{% endstep %}

{% step %}
### Checking the website

Open your store and check that everything works.

{% hint style="info" %}
The previous version stays in <kbd>/var/www/accent-store-prev</kbd>, in case you need to go back.
{% endhint %}
{% endstep %}
{% endstepper %}
