---
description: >-
  How to host a resource pack for your Minecraft server, so every player gets
  your custom models and textures when they join.
---

# How do I host a resource pack for my Minecraft server?

**Short answer:** if you use **ItemsAdder**, **Nexo** or **Oraxen**, the plugin builds the pack and can send it to players for you, you only set it up once. Without such a plugin, upload the pack somewhere with a **direct download link** and add that link to `server.properties`.

***

### With a custom item plugin

| Plugin     | How the pack reaches players                                                           |
| ---------- | -------------------------------------------------------------------------------------- |
| ItemsAdder | Choose a hosting option once in ItemsAdder's settings, see [ItemsAdder's wiki](https://itemsadder.devs.beer/). |
| Nexo       | Sends the pack to players by itself.                                                   |
| Oraxen     | Sends the pack to players by itself.                                                   |

### Without a plugin

1. Upload your pack `.zip` to a host that gives a **direct download link** (the link must download the file, not open a web page).
2. In `server.properties`, set:

```
resource-pack=https://your-link/pack.zip
require-resource-pack=true
```

3. Restart your server.

{% hint style="info" %}
Changed the pack? Players may keep the old one. Adding the pack's SHA-1 checksum in `resource-pack-sha1` makes Minecraft download the new version.
{% endhint %}

Players don't get the pack? See [Why are my custom items purple and black?](why-are-my-custom-items-purple-and-black.md)

***

### Our model packs

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Halloween Model Pack</strong></td><td>Skulls, gravestones, witches and more for ItemsAdder, Nexo and Oraxen.</td><td><a href="https://builtbybit.com/resources/halloween-model-pack.37401/">https://builtbybit.com/resources/halloween-model-pack.37401/</a></td></tr><tr><td><strong>Arcade - Tool Pack</strong></td><td>A full set of arcade tools with an 80s hat cosmetic.</td><td><a href="https://builtbybit.com/resources/arcade-tool-pack.132955/">https://builtbybit.com/resources/arcade-tool-pack.132955/</a></td></tr></tbody></table>
