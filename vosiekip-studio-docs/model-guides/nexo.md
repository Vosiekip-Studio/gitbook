---
description: >-
  This page will walk us through installing our models with the Nexo
  plugin.
---

# Nexo

Make sure [Nexo](https://docs.nexomc.com/) is installed and has started at least once, so its folders exist. New to our models? Read the [installation guide →](installation-guide.md) first.

***

{% stepper %}
{% step %}
### Finding the Nexo folder

1. Unzip the model download on your computer.
2. Open <kbd>0. Configs/Nexo</kbd>.
3. Inside you'll find an `items` folder and a `pack` folder. Some packs also have a `glyphs` folder.
{% endstep %}

{% step %}
### Uploading the files

Copy each folder into the folder with the same name on your server:

| From the download | To your server                   |
| ----------------- | -------------------------------- |
| `items`           | <kbd>plugins/Nexo/items</kbd>    |
| `pack`            | <kbd>plugins/Nexo/pack</kbd>     |
| `glyphs` (if there is one) | <kbd>plugins/Nexo/glyphs</kbd> |

1. Open your server's files (File Manager or SFTP).
2. Open the `items` folder from the download and upload what's **inside** it to <kbd>plugins/Nexo/items</kbd>.
3. Do the same for `pack` and, if there is one, `glyphs`.

<!-- Screenshot: plugins/Nexo with items and pack folders -->

{% hint style="warning" %}
**Add** the files to the folders that are already there, don't replace the whole folder. Otherwise you delete the items and models you already have.
{% endhint %}
{% endstep %}

{% step %}
### Reloading Nexo

In your server console or in game, run:

```
/nexo reload
```

Nexo loads the new items and builds a new resource pack with the models in it.

{% hint style="info" %}
Nexo sends the resource pack to players by itself. Players who are online may need to rejoin to get the new pack.
{% endhint %}
{% endstep %}

{% step %}
### Getting the models in game

1. Rejoin the server and accept the resource pack when Minecraft asks.
2. Run `/nexo inv` to open the Nexo item menu and find the items of the pack.

You can also give an item with:

```
/nexo give <item> [amount] [player]
```

For example, the tombstone from our Halloween pack: `/nexo give halloween_tombstone 1 Steve`. The item names are listed in the menu.
{% endstep %}
{% endstepper %}

***

<details>

<summary>The models are purple and black</summary>

The resource pack doesn't have the textures yet.

* Check that the files from `pack` are inside <kbd>plugins/Nexo/pack</kbd>, and not in an extra folder such as `plugins/Nexo/pack/pack`.
* Run `/nexo reload` again and rejoin.

</details>

<details>

<summary>I don't get the resource pack when I join</summary>

In Minecraft, open **Multiplayer**, select your server, press **Edit** and set **Server Resource Packs** to **Enabled**.

</details>
