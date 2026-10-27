---
description: >-
  How to protect your Minecraft server spawn from griefing with WorldGuard:
  make a region and stop building, explosions and PvP.
---

# How do I protect my spawn from griefing?

**Short answer:** use the free **WorldGuard** plugin (with WorldEdit or FastAsyncWorldEdit). Select your spawn, turn it into a **region**, and set **flags** that stop building and explosions.

***

{% stepper %}
{% step %}
### Install the plugins

Install **WorldEdit** (or FastAsyncWorldEdit) and **WorldGuard** on your server, then restart.
{% endstep %}

{% step %}
### Select your spawn

1. Run `//wand` to get the selection tool.
2. Left-click one corner of your spawn and right-click the opposite corner.
3. Run `//expand vert` so the region goes from the bottom of the world to the sky.
{% endstep %}

{% step %}
### Create the region

```
/rg define spawn
```
{% endstep %}

{% step %}
### Set flags

Players without permission can't build in a region by default. To also stop explosions and PvP:

```
/rg flag spawn tnt deny
/rg flag spawn creeper-explosion deny
/rg flag spawn pvp deny
```
{% endstep %}
{% endstepper %}

{% hint style="info" %}
**Lifesteal or PvP spawn?** Make a separate region for the arena with `pvp allow`, inside the spawn region. Give it a higher priority with `/rg setpriority arena 10`.
{% endhint %}

***

### Our spawns

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Spawn - Holiday Lifesteal</strong></td><td>501×501 lifesteal spawn with a themed arena, crates and a circle spawn point.</td><td><a href="https://builtbybit.com/resources/spawn-holiday-lifesteal.115529/">https://builtbybit.com/resources/spawn-holiday-lifesteal.115529/</a></td></tr><tr><td><strong>Spawn - Oriental Lifesteal</strong></td><td>501×501 lifesteal spawn with an oriental theme, crates and a circle spawn point.</td><td><a href="https://builtbybit.com/resources/spawn-oriental-lifesteal.115530/">https://builtbybit.com/resources/spawn-oriental-lifesteal.115530/</a></td></tr><tr><td><strong>Spawn - Dinosaur Lifesteal</strong></td><td>501×501 lifesteal spawn with a dinosaur arena, crates and a circle spawn point.</td><td><a href="https://builtbybit.com/resources/spawn-dinosaur-lifesteal.113396/">https://builtbybit.com/resources/spawn-dinosaur-lifesteal.113396/</a></td></tr><tr><td><strong>Spawn - Multibiome Lifesteal</strong></td><td>501×501 lifesteal spawn with a multibiome arena, crates and a circle spawn point.</td><td><a href="https://builtbybit.com/resources/spawn-multibiome-lifesteal.110069/">https://builtbybit.com/resources/spawn-multibiome-lifesteal.110069/</a></td></tr><tr><td><strong>Spawn - Orange Village</strong></td><td>Medieval village spawn with an iconic portal and a cute market.</td><td><a href="https://builtbybit.com/resources/spawn-orange-village.112998/">https://builtbybit.com/resources/spawn-orange-village.112998/</a></td></tr><tr><td><strong>Spawn - Blue Village</strong></td><td>Medieval village spawn with an iconic portal and large gold piles.</td><td><a href="https://builtbybit.com/resources/spawn-blue-village.112989/">https://builtbybit.com/resources/spawn-blue-village.112989/</a></td></tr></tbody></table>
