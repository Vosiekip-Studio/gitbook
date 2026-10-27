---
description: >-
  This page will walk us through pasting one of our builds into your world
  with FastAsyncWorldEdit.
---

# Pasting with FAWE

[FastAsyncWorldEdit](https://www.spigotmc.org/resources/13932/) (FAWE) is a faster version of WorldEdit that can paste big builds without freezing your server. New to our builds? Read the [installation guide →](installation-guide.md) first, it explains which file to pick.

{% hint style="info" %}
On this page we write the name of your schematic file as `<build>`. For example, for `spawn_holiday_lifesteal_to_1.21.9.schem` that is `spawn_holiday_lifesteal_to_1.21.9`.
{% endhint %}

***

{% stepper %}
{% step %}
### Installing FAWE

1. Download [FastAsyncWorldEdit](https://www.spigotmc.org/resources/13932/) for your server version.
2. Upload the `.jar` file to your server's <kbd>plugins</kbd> folder.
3. Restart your server.

Already using normal WorldEdit? That works too, only big builds paste slower. Use <kbd>plugins/WorldEdit/schematics</kbd> instead of the FAWE folder in the next step.
{% endstep %}

{% step %}
### Uploading the schematic

1. Open <kbd>0. Assets/Schematics</kbd> in the download and find the file for your Minecraft version.
2. Open your server's files (File Manager or SFTP).
3. Go to <kbd>plugins/FastAsyncWorldEdit/schematics</kbd>. No `schematics` folder? Create it.
4. Upload the schematic file there.

<!-- Screenshot: plugins/FastAsyncWorldEdit/schematics with the build file -->

{% hint style="warning" %}
Upload only the **one** file for your version, not the whole `Schematics` folder.
{% endhint %}
{% endstep %}

{% step %}
### Loading the schematic

Join your server, go to the world where you want the build, and run:

```
//schem load <build>
```

For example `//schem load spawn_holiday_lifesteal_to_1.21.9`. You don't need to type `.schem` at the end.

<details>

<summary>It says the schematic doesn't exist</summary>

* Run `//schem list` to see the files FAWE can find, and check the spelling.
* Check that the file is directly inside the `schematics` folder.

</details>
{% endstep %}

{% step %}
### Pasting the build

1. Fly to an **empty, open area**. Builds are big, so leave plenty of space around you.
2. Stand where you want the build and run:

```
//paste
```

FAWE places the build next to where you're standing. It may take a few seconds for big builds.

{% hint style="info" %}
**Wrong spot?** Run `//undo` to remove it, move, and paste again.
{% endhint %}

<details>

<summary>Paste without the empty space around the build</summary>

`//paste` also pastes the air around the build, which clears anything that was already there. Use this instead to only paste the blocks:

```
//paste -a
```

</details>
{% endstep %}

{% step %}
### Setting your spawn

Want players to arrive at the build when they join? Stand where they should appear and run:

```
/setworldspawn
```

Using a spawn plugin, such as EssentialsX? Use its own command instead, for example `/setspawn`.
{% endstep %}
{% endstepper %}
