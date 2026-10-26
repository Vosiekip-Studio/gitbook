---
description: >-
  This page will walk us through uploading files to your hosting or server
  with FileZilla.
---

# Connecting with SFTP

SFTP lets you move files from your computer to your hosting or server, just like dragging files between folders. We use [FileZilla](https://filezilla-project.org/), a free app for Windows, macOS and Linux.

{% hint style="info" %}
On a **hosting panel** you can also upload with the panel's **File Manager**, you don't need FileZilla. On a **VPS** you do need an SFTP app like FileZilla.
{% endhint %}

***

{% stepper %}
{% step %}
### Installing FileZilla

1. Go to [filezilla-project.org](https://filezilla-project.org/).
2. Press <mark style="color:$primary;">**Download FileZilla Client**</mark>. Make sure you pick the **Client**, not the Server.
3. Open the downloaded file and follow the installer.

{% hint style="warning" %}
The FileZilla installer may offer extra software during the setup. Press **Decline** or **Skip** for these offers, you only need FileZilla itself.
{% endhint %}
{% endstep %}

{% step %}
### Finding your login details

You need four things to connect. Pick the tab that matches your hosting.

{% tabs %}
{% tab title="VPS" %}
| Field    | What to fill in                                                    |
| -------- | ------------------------------------------------------------------ |
| Host     | `sftp://YOUR_SERVER_IP`                                            |
| Username | `root`                                                             |
| Password | your server's root password, from your VPS provider's welcome email |
| Port     | `22`                                                               |
{% endtab %}

{% tab title="Hosting panel" %}
| Field    | What to fill in                                                 |
| -------- | --------------------------------------------------------------- |
| Host     | `sftp://` followed by your domain, e.g. `sftp://store.example.com` |
| Username | your hosting account username (`USER`)                          |
| Password | your hosting account password                                   |
| Port     | `22`                                                            |

{% hint style="info" %}
SFTP on a hosting panel only works if your plan has **SSH access** turned on. If you can't connect, use the panel's **File Manager** instead, or ask your host to turn on SSH.
{% endhint %}
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Connecting

1. Open FileZilla.
2. Fill in **Host**, **Username**, **Password** and **Port** in the bar at the top of the window.
3. Press <mark style="color:$primary;">**Quickconnect**</mark>.
4. The first time, FileZilla asks if you trust the server ("Unknown host key"). Tick **Always trust this host** and press <mark style="color:$primary;">**OK**</mark>.

<!-- Screenshot: FileZilla Quickconnect bar filled in -->

<details>

<summary>It doesn't connect</summary>

* Check that the host starts with `sftp://` and the port is `22`.
* Check your username and password, they are case sensitive.
* **VPS:** make sure your server is running in your provider's dashboard.
* **Hosting panel:** your plan may not have SSH access, use **File Manager** instead.

</details>
{% endstep %}

{% step %}
### Uploading files

Once connected, FileZilla shows two sides:

| Left side                 | Right side                    |
| ------------------------- | ----------------------------- |
| Your computer             | Your server or hosting        |

1. On the **right side**, go to the folder the guide tells you. For example type <kbd>/var/www</kbd> in the **Remote site** box and press **Enter**.
2. On the **left side**, find the file on your computer, for example <kbd>&lt;theme&gt;-store.zip</kbd> in your Downloads folder.
3. Drag the file from the left side to the right side.
4. Wait until the transfer at the bottom of the window is finished.

<!-- Screenshot: FileZilla with a file dragged from left to right -->

{% hint style="info" %}
**Next time:** press the small arrow next to **Quickconnect** to pick your server again, you don't have to type everything again.
{% endhint %}
{% endstep %}
{% endstepper %}

***

Done uploading? Go back to your guide: [Hosting panel install](hosting-panel-install.md) or [VPS install](vps-install.md).
