---
description: >-
  This page will walk us through installing any of our Minecraft builds on
  your server, and help you pick the right method.
---

# Installation guide

Every build download comes in two forms: a **schematic** you paste with FastAsyncWorldEdit, and a ready-made **world folder**. Both give you the same build, pick the one that suits you.

***

{% stepper %}
{% step %}
### Gather what you need

* **A Minecraft Java server.**
* **Our build download** from BuiltByBit, see [How to download →](../how-to-download.md).
* **Access to your server's files**, through your Minecraft host's **File Manager** or with SFTP.
{% endstep %}

{% step %}
### Unzip the download

1. Unzip the downloaded build on your computer. On Windows: right-click → **Extract All**. On macOS: double-click the file.
2. Open the `0. Assets` folder. Inside you'll find two folders:
   * `Schematics`: the build as a schematic file, for pasting with FastAsyncWorldEdit.
   * `Worldfiles`: the build as a complete world folder.
{% endstep %}

{% step %}
### Find your Minecraft version

Every build comes in a version for each Minecraft version. The files end with `_to_` and a version number, for example:

* `spawn_holiday_lifesteal_to_1.21.9.schem`
* `spawn_holiday_lifesteal_to_1.21.9` (world folder)

**Pick the file with your server's version.** Is your exact version not in the list? Then pick the closest version **below** yours.

| Your server version | Pick the file ending in |
| ------------------- | ----------------------- |
| `1.21.9`            | `_to_1.21.9`            |
| `1.21.8`            | `_to_1.21.6` (the closest one below) |
| `1.20.1`            | `_to_1.20`              |

{% hint style="warning" %}
Never use a version **higher** than your server. Minecraft can't load a build made for a newer version.
{% endhint %}

<details>

<summary>Where do I find my server's version?</summary>

* Run `/version` in your server console or in game.
* Or look at your Minecraft host's panel, most show the version on the overview page.

</details>
{% endstep %}

{% step %}
### Pick your method

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Paste with FAWE</strong> (recommended)</td><td>Paste the build into a world you already have. Works while the server is running.</td><td><a href="pasting-with-fawe.md">pasting-with-fawe.md</a></td></tr><tr><td><strong>Upload the world folder</strong></td><td>Add the build as its own world, exactly as we built it. Needs a server restart.</td><td><a href="uploading-the-world-folder.md">uploading-the-world-folder.md</a></td></tr></tbody></table>

<details>

<summary>Which one should I pick?</summary>

* **You want the build inside an existing world**, such as next to your current spawn → [Paste with FAWE](pasting-with-fawe.md).
* **You want the build as a separate world**, for example a spawn world players teleport to → [Upload the world folder](uploading-the-world-folder.md).

</details>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Stuck somewhere? Don't hesitate to [reach out on Discord](https://discord.gg/PxwaKxKhb6), we're here to help.
{% endhint %}
