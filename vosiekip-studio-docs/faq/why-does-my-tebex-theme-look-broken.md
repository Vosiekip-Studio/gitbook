---
description: >-
  Your Tebex theme looks broken or unstyled after installing it? The most
  common causes and how to fix each one.
---

# Why does my Tebex theme look broken after installing it?

**Short answer:** almost always, a file wasn't **saved** or an **asset** wasn't uploaded correctly. Go through the checklist below, it fixes nearly every broken theme.

***

### Checklist

{% stepper %}
{% step %}
### Every file is saved

When you paste a theme file over the default one, press <mark style="color:$primary;">**Ctrl + S**</mark> before you open the next file. A file that isn't saved keeps the default code, which breaks the theme.

Open each file again and check it starts with the theme's code, not Tebex's default code.
{% endstep %}

{% step %}
### The CSS and JavaScript assets are uploaded with the right type

* `store.css` must be uploaded as a **CSS** asset.
* `function.js` must be uploaded as a **JAVASCRIPT** asset.

Uploaded with the wrong type, or not at all? The store has no styling or nothing works when you click.
{% endstep %}

{% step %}
### The header and footer are replaced

`header.twig` and `footer.twig` must be pasted over the existing files and saved, just like the webstore files.
{% endstep %}

{% step %}
### The schema is uploaded

Without the schema, the theme's settings don't exist and the store can look empty. See [Why are my theme settings not showing?](why-are-my-tebex-theme-settings-not-showing.md)
{% endstep %}

{% step %}
### The template is the one your store uses

In **Appearance**, check that the template you edited is the one your store is using, not the default template.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
**New Tebex store?** Custom themes can't be used on new stores right now. See [Can I use a Tebex theme on a new Tebex store?](can-i-use-a-tebex-theme-on-a-new-tebex-store.md)
{% endhint %}

Still stuck? Follow the full [Tebex theme installation guide →](../tebex-theme-guides/installation-guide.md) again, or [ask us on Discord](https://discord.gg/PxwaKxKhb6).
