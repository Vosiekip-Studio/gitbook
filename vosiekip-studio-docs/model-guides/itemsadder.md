---
description: >-
  This page will walk us through installing our models with the ItemsAdder
  plugin.
---

# ItemsAdder

Make sure [ItemsAdder](https://www.spigotmc.org/resources/73355/) is installed and has started at least once, so its folders exist. New to our models? Read the [installation guide →](installation-guide.md) first.

***

{% stepper %}
{% step %}
### Finding the ItemsAdder folder

1. Unzip the model download on your computer.
2. Open <kbd>0. Configs/Itemsadder/Contents</kbd>.
3. Inside you'll find one folder with the name of the model pack, for example `halloweenpack`. On this page we write that name as `<model-pack>`. This is the folder we upload.

{% hint style="warning" %}
Upload the `<model-pack>` folder itself: not the files inside it, and not the `Contents` folder around it. ItemsAdder needs the pack folder to know which pack the files belong to.
{% endhint %}
{% endstep %}

{% step %}
### Uploading the files

1. Open your server's files (File Manager or SFTP).
2. Go to <kbd>plugins/ItemsAdder/contents</kbd>.
3. Upload the pack folder there.

You should now have a folder such as <kbd>plugins/ItemsAdder/contents/&lt;model-pack&gt;</kbd>, with the folders `items_packs` and `resource_pack` inside.

<!-- Screenshot: plugins/ItemsAdder/contents with the pack folder -->

<details>

<summary>I don't have a contents folder</summary>

* Start your server once with ItemsAdder installed, it creates the folder on the first start.
* Still not there? You're using a very old ItemsAdder version (3.2.5 or older). Update ItemsAdder to the latest version.

</details>
{% endstep %}

{% step %}
### Building the resource pack

Players need the resource pack to see the models. In your server console or in game, run:

```
/iazip
```

ItemsAdder builds a new resource pack with the models in it. Wait until it says it's done.

{% hint style="info" %}
**Using ItemsAdder for the first time?** It must also know how to send the pack to players. Follow ItemsAdder's own **resource pack hosting** setup in its [wiki](https://itemsadder.devs.beer/) once, after that `/iazip` is all you need.
{% endhint %}
{% endstep %}

{% step %}
### Getting the models in game

1. Rejoin the server, or run `/iareload`, so you get the new resource pack.
2. Accept the resource pack when Minecraft asks.
3. Run `/ia` to open the ItemsAdder menu and find the items of the pack.

You can also give an item with:

```
/iaget <model-pack>:<item>
```

Change `<model-pack>` to the name of your pack folder. For example, the tombstone from our Halloween pack is `/iaget halloweenpack:halloweenpack_1`. The item names are listed in the menu.
{% endstep %}
{% endstepper %}

***

<details>

<summary>The models are purple and black</summary>

The resource pack doesn't have the textures yet.

* Run `/iazip` again and rejoin.
* Check that the pack folder is directly inside `contents`, not one folder deeper.

</details>

<details>

<summary>I don't get the resource pack when I join</summary>

* Make sure ItemsAdder's resource pack hosting is set up (see step 3).
* In Minecraft, open **Multiplayer**, select your server, press **Edit** and set **Server Resource Packs** to **Enabled**.

</details>
