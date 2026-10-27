---
description: >-
  This page will walk us through adding one of our builds to your server as
  its own world.
---

# Uploading the world folder

The world folder is the build exactly as we made it, already placed in its own world. New to our builds? Read the [installation guide →](installation-guide.md) first, it explains which folder to pick.

***

{% stepper %}
{% step %}
### Preparing the world folder

1. Open <kbd>0. Assets/Worldfiles</kbd> in the download and find the folder for your Minecraft version, for example `spawn_holiday_lifesteal_to_1.21.9`.
2. Rename the folder to a short name without spaces, for example `spawn`. This becomes the name of the world on your server.

{% hint style="info" %}
On this page we use `spawn` as the world name. Picked another name? Use that wherever you see `spawn`.
{% endhint %}
{% endstep %}

{% step %}
### Uploading the folder

1. **Stop your server.** Minecraft can overwrite worlds that change while it's running.
2. Open your server's files (File Manager or SFTP).
3. Upload the `spawn` folder to the **main folder** of your server: the same place where your `world` folder and `server.properties` are.

You should now have <kbd>spawn/level.dat</kbd> next to your other worlds.

<!-- Screenshot: server main folder with the spawn world next to world -->

<details>

<summary>My web File Manager can't upload folders</summary>

Zip the `spawn` folder on your computer, upload the zip to the main folder, then use the File Manager's **Unarchive** (or **Extract**) option. Or use SFTP, see [Connecting with SFTP](../tebex-website-guides/connecting-with-sftp.md).

</details>

{% hint style="warning" %}
Make sure the folder isn't doubled, such as `spawn/spawn/level.dat`. The `level.dat` file must be directly inside the `spawn` folder.
{% endhint %}
{% endstep %}

{% step %}
### Loading the world

Pick how you want to use the world.

{% tabs %}
{% tab title="As an extra world (recommended)" %}
Keep your current world and add the build as a second world, using the free [Multiverse-Core](https://www.spigotmc.org/resources/390/) plugin.

1. Install Multiverse-Core: upload the `.jar` file to your <kbd>plugins</kbd> folder.
2. Start your server.
3. In the server console, run:

```
mv import spawn normal
```

4. In game, go to the world with:

```
/mv tp spawn
```
{% endtab %}

{% tab title="As your main world" %}
Replace your main world with the build. Players spawn in it when they join.

1. Open <kbd>server.properties</kbd> in your server's main folder.
2. Find the line `level-name=world` and change it to:

```
level-name=spawn
```

3. Save the file and start your server.

{% hint style="warning" %}
Your old world isn't deleted, but players no longer see it. Change `level-name` back to `world` to return to it.
{% endhint %}
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Setting your spawn

Stand where players should appear in the new world and run:

```
/setworldspawn
```

Using a spawn plugin, such as EssentialsX? Use its own command instead, for example `/setspawn`.
{% endstep %}
{% endstepper %}

***

<details>

<summary>The world is empty or a new world was generated</summary>

* Check that `level.dat` is directly inside the folder (see step 2).
* Check that you picked the folder for your Minecraft version, not a newer one.
* Check that the folder name matches the name in your command or in `level-name`, they are case sensitive.

</details>
