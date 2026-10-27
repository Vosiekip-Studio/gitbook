---
description: >-
  Your Tebex theme settings don't show up under Appearance? Upload the theme's
  schema file, here is how.
---

# Why are my theme settings not showing in Tebex?

**Short answer:** the theme's **schema** isn't uploaded. The schema is the file that creates all the theme settings, such as colors, texts and add-ons.

***

### How to upload the schema

1. Open your template in the Tebex **template editor**.
2. At the top, press <mark style="color:$primary;">**"&lt;/&gt; Change schema"**</mark>.
3. Open the schema file from your download in a code editor, such as [Visual Studio Code](https://code.visualstudio.com/download). You'll find it in <kbd>0. Theme/Schema-files</kbd>.
4. Copy everything: <mark style="color:$primary;">**Ctrl + A**</mark>, then <mark style="color:$primary;">**Ctrl + C**</mark>.
5. In Tebex, select everything in the schema and paste over it: <mark style="color:$primary;">**Ctrl + A**</mark>, then <mark style="color:$primary;">**Ctrl + V**</mark>.
6. Save: <mark style="color:$primary;">**Ctrl + S**</mark>.

Go back to **Appearance**, the theme settings now show up.

{% hint style="info" %}
The schema is the step people skip most often. Always upload it, even if the store already looks right.
{% endhint %}

See step 6 of the [Tebex theme installation guide →](../tebex-theme-guides/installation-guide.md) for screenshots.
