---
description: >-
  Custom items, furniture or blocks show up purple and black on your Minecraft
  server? What it means and how to fix it in ItemsAdder, Nexo and Oraxen.
---

# Why are my custom items purple and black?

**Short answer:** the purple and black checkerboard means Minecraft **can't find the texture**. Usually the resource pack wasn't rebuilt after adding the files, the player didn't get the new pack, or a file is in the wrong folder.

***

### Checklist

{% stepper %}
{% step %}
### Rebuild the resource pack

After adding new files, rebuild the pack:

| Plugin     | Command              |
| ---------- | -------------------- |
| ItemsAdder | `/iazip`             |
| Nexo       | `/nexo reload`       |
| Oraxen     | `/oraxen reload all` |
{% endstep %}

{% step %}
### Get the new pack

Rejoin the server and accept the resource pack. In Minecraft, check that **Server Resource Packs** is set to **Enabled** for your server (**Multiplayer → Edit**).
{% endstep %}

{% step %}
### Check the folders

* **ItemsAdder:** the pack folder must be directly inside `plugins/ItemsAdder/contents`, not one folder deeper.
* **Nexo / Oraxen:** the files from `pack` must be inside `plugins/Nexo/pack` or `plugins/Oraxen/pack`, not in an extra `pack/pack` folder.
{% endstep %}

{% step %}
### Check file names

File and folder names must be **lowercase** and have **no spaces**. `My Model.png` doesn't work, `my_model.png` does.
{% endstep %}
{% endstepper %}

Step by step per plugin: [model installation guide →](../model-guides/installation-guide.md)

***

### Our model packs

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="image">Cover image</th></tr></thead><tbody><tr><td><strong>Halloween Model Pack</strong></td><td>Skulls, gravestones, witches and more for ItemsAdder, Nexo and Oraxen.</td><td><a href="https://builtbybit.com/resources/halloween-model-pack.37401/">https://builtbybit.com/resources/halloween-model-pack.37401/</a></td><td><a href="../.gitbook/assets/product-halloween-model-pack.jpg">product-halloween-model-pack.jpg</a></td></tr><tr><td><strong>Arcade - Tool Pack</strong></td><td>A full set of arcade tools with an 80s hat cosmetic.</td><td><a href="https://builtbybit.com/resources/arcade-tool-pack.132955/">https://builtbybit.com/resources/arcade-tool-pack.132955/</a></td><td><a href="../.gitbook/assets/product-arcade-tool-pack.jpg">product-arcade-tool-pack.jpg</a></td></tr></tbody></table>
