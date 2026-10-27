---
description: >-
  Your rank table, upsell or gift card section is empty in your Tebex theme?
  Usually the category or package ID is wrong. Here is how to fix it.
---

# Why is my rank table, upsell or gift card section empty?

**Short answer:** the add-on can't find your packages. Check that you entered the right **category ID** or **package IDs** in the add-on settings, and that the category has packages in it.

***

### Rank table

1. Go to [creator.tebex.io/packages](https://creator.tebex.io/packages) and find your ranks category.
2. Copy its **category ID**, the number in the link (for example `/category/12` → `12`).
3. In [Appearance](https://creator.tebex.io/appearance), open **Rank category (Addon)** and paste the ID.
4. Fill in the rank features in the `ranktable.twig` file, as explained inside the file.

### Upsell and coin slider

* Enter the **parent package ID** (the key or package players start from).
* Enter the **upsell package IDs** in order, separated by commas, for example `7170425,7170426,7170427`.

### Gift cards

* Enter the **category ID** of your gift card category.
* The category needs **five** gift card packages to match the preview.

{% hint style="info" %}
Packages that are hidden or disabled in Tebex don't show up in the add-ons either.
{% endhint %}

### Using one of our Tebex websites?

There you pick the category from a list, so a wrong ID isn't possible. Empty? Check that the category has packages, then press **System → Sync now** in the admin panel. See [Add-ons](../tebex-website-guides/add-ons.md).
