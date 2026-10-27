---
description: >-
  This page will walk us through installing our models with the Oraxen
  plugin.
---

# Oraxen

Make sure [Oraxen](https://docs.oraxen.com/) is installed and has started at least once, so its folders exist. New to our models? Read the [installation guide →](installation-guide.md) first.

***

{% stepper %}
{% step %}
### Finding the Oraxen folder

1. Unzip the model download on your computer.
2. Open the `Oraxen` folder inside it.
3. Inside you'll find an `items` folder and a `pack` folder.
{% endstep %}

{% step %}
### Uploading the files

Copy each folder into the folder with the same name on your server:

| From the download | To your server                  |
| ----------------- | ------------------------------- |
| `items`           | <kbd>plugins/Oraxen/items</kbd> |
| `pack`            | <kbd>plugins/Oraxen/pack</kbd>  |

1. Open your server's files (File Manager or SFTP).
2. Open the `items` folder from the download and upload what's **inside** it to <kbd>plugins/Oraxen/items</kbd>.
3. Do the same for `pack`.

<!-- Screenshot: plugins/Oraxen with items and pack folders -->

{% hint style="warning" %}
**Add** the files to the folders that are already there, don't replace the whole folder. Otherwise you delete the items and models you already have.
{% endhint %}
{% endstep %}

{% step %}
### Reloading Oraxen

In your server console or in game, run:

```
/oraxen reload all
```

Oraxen loads the new items and builds a new resource pack with the models in it.

{% hint style="info" %}
Oraxen sends the resource pack to players by itself. Players who are online can get the new pack right away with `/oraxen pack send @a`, or by rejoining.
{% endhint %}
{% endstep %}

{% step %}
### Getting the models in game

1. Rejoin the server and accept the resource pack when Minecraft asks.
2. Run `/oraxen inv` to open the Oraxen item menu and find the items of the pack.

You can also give an item with:

```
/oraxen give <player> <item> [amount]
```

For example `/oraxen give Steve common_key 1`. The item names are listed in the menu.
{% endstep %}
{% endstepper %}

***

<details>

<summary>The models are purple and black</summary>

The resource pack doesn't have the textures yet.

* Check that the files from `pack` are inside <kbd>plugins/Oraxen/pack</kbd>, and not in an extra folder such as `plugins/Oraxen/pack/pack`.
* Run `/oraxen reload all` again and rejoin.

</details>

<details>

<summary>I don't get the resource pack when I join</summary>

In Minecraft, open **Multiplayer**, select your server, press **Edit** and set **Server Resource Packs** to **Enabled**.

</details>
