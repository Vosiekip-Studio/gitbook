---
description: >-
  This page will walk us through installing any of our Minecraft models on
  your server, and help you pick the right guide for your plugin.
---

# Installation guide

Our models work with three popular custom item plugins: **ItemsAdder**, **Nexo** and **Oraxen**. You only need **one** of them on your server. Each download contains a ready-made folder for every plugin, so you just copy the right folder into your server.

***

{% stepper %}
{% step %}
### Gather what you need

* **A Minecraft Java server** running Paper (or a fork of it, such as Purpur).
* **One custom item plugin** installed: [ItemsAdder](https://www.spigotmc.org/resources/73355/), [Nexo](https://docs.nexomc.com/) or [Oraxen](https://docs.oraxen.com/).
* **Our model download** from BuiltByBit, see [How to download →](../how-to-download.md).
* **Access to your server's files**, through your Minecraft host's **File Manager** or with SFTP.

{% hint style="info" %}
Not sure which plugin you have? Look in your server's `plugins` folder. You will see a folder called `ItemsAdder`, `Nexo` or `Oraxen`.
{% endhint %}
{% endstep %}

{% step %}
### Unzip the download

1. Unzip the downloaded model file on your computer. On Windows: right-click → **Extract All**. On macOS: double-click the file.
2. Open the `0. Configs` folder. Inside you'll find a folder for each plugin: `ItemsAdder`, `Nexo` and `Oraxen`.
3. Open the folder for the plugin **you** use. The other folders you can ignore.
{% endstep %}

{% step %}
### Pick your plugin guide

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>ItemsAdder</strong></td><td>Copy one folder into <code>contents</code>, then run <code>/iazip</code>.</td><td><a href="itemsadder.md">itemsadder.md</a></td></tr><tr><td><strong>Nexo</strong></td><td>Copy the <code>items</code> and <code>pack</code> folders, then run <code>/nexo reload</code>.</td><td><a href="nexo.md">nexo.md</a></td></tr><tr><td><strong>Oraxen</strong></td><td>Copy the <code>items</code> and <code>pack</code> folders, then run <code>/oraxen reload all</code>.</td><td><a href="oraxen.md">oraxen.md</a></td></tr></tbody></table>
{% endstep %}
{% endstepper %}

***

<details>

<summary>How do I upload files to my Minecraft server?</summary>

Most Minecraft hosts have a **File Manager** in their panel:

1. Log in to your host's panel and open **Files** (or **File Manager**).
2. Go to the folder the guide tells you, for example <kbd>plugins/ItemsAdder/contents</kbd>.
3. Press **Upload** and select the files, or drag them into the page.

Uploading a whole folder can be slow in a web panel. With many files, use SFTP instead: your host shows the SFTP address, username and port in the panel, and [FileZilla works the same way](../tebex-website-guides/connecting-with-sftp.md) as for a website.

</details>

{% hint style="info" %}
Stuck somewhere? Don't hesitate to [reach out on Discord](https://discord.gg/PxwaKxKhb6), we're here to help.
{% endhint %}
