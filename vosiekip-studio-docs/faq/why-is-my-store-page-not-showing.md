---
description: >-
  Your vote, staff, patron, FAQ or rules page doesn't show up in your Tebex
  theme? Check these three things.
---

# Why is my vote, staff, patron or FAQ page not showing?

**Short answer:** the page title in Tebex must match the **page title setting** of the add-on **exactly**, including capital letters. `Vote` and `vote` are not the same.

***

### Checklist

1. **The page asset is uploaded.** In the template editor, the page's `.twig` file (for example `vote-page.twig`) must be uploaded as a **TWIG** asset, with the same file name as in the download.
2. **The Tebex page exists.** Create a page in Tebex here: [creator.tebex.io/pages](https://creator.tebex.io/pages). FAQ & Rules need two pages.
3. **The titles match exactly.** In [Appearance](https://creator.tebex.io/appearance), open the add-on (for example **Vote Page (Addon)**) and type the page title exactly as you named the page in Tebex.

{% hint style="warning" %}
Watch out for spaces at the end of a title. `Vote ` (with a space) doesn't match `Vote`.
{% endhint %}

### Using one of our Tebex websites?

The same rule applies: the Tebex page title must match the add-on's **page title** setting, then turn the page on in the add-on's tab. See [Add-ons](../tebex-website-guides/add-ons.md).

***

More details per page: [Tebex theme installation guide → Setting up Extras](../tebex-theme-guides/installation-guide.md).
