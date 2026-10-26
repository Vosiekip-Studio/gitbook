---
description: >-
  This page will walk us through installing and setting up add-ons for your
  Tebex website.
---

# Add-ons

Add-ons add extra pages and features to your website. Each add-on is its own zip file, you only install the ones you want. The file names start with the name of your theme, written here as `<theme>`.

| Add-on                      | File                                                  |
| --------------------------- | ----------------------------------------------------- |
| Rank Table                  | `<theme>-store-rank-table-addon.zip`                   |
| Patron Page                 | `<theme>-store-patron-page-addon.zip`                  |
| Vote Page                   | `<theme>-store-vote-page-addon.zip`                    |
| FAQ & Rules                 | `<theme>-store-faq-and-rules-addon.zip`                |
| Key Upselling & Coin Slider | `<theme>-store-upselling-and-coin-slider-addon.zip`    |
| Gift Cards                  | `<theme>-store-giftcards-addon.zip`                    |
| Staff Team Page             | `<theme>-store-staff-team-page-addon.zip`              |

***

{% stepper %}
{% step %}
### Uploading the add-on

Pick the tab that matches how you installed the website. The examples use the **FAQ & Rules** add-on, repeat the steps for each add-on you want.

{% tabs %}
{% tab title="Hosting panel" %}
1. In **File Manager**, open <kbd>tebex-store/theme</kbd>. If there is no `extras` folder, create one.
2. Open `extras` and upload the add-on zip there.
3. Right-click the zip, press <mark style="color:$primary;">**Extract**</mark>, and extract it right there in <kbd>tebex-store/theme/extras</kbd>.
4. Delete the zip. You should now have a folder such as <kbd>tebex-store/theme/extras/faq-and-rules</kbd>.
5. Press <mark style="color:$primary;">**Restart**</mark> on the Node.js app page.

{% hint style="info" %}
Unlike the website itself, the add-on zips contain no JavaScript, so the panel's upload scanner accepts them.
{% endhint %}
{% endtab %}

{% tab title="VPS" %}
1. Upload the add-on zip to <kbd>/var/www/</kbd> with your SFTP client.
2. Run these commands. For other add-ons, also change `faq-and-rules` to the add-on you are installing.

{% hint style="warning" %}
**Change `<theme>` to the name of your theme** before you run these commands, it must match the file you uploaded.

Example: if your file is called `mytheme-store-faq-and-rules-addon.zip`, then this line:

`unzip /var/www/<theme>-store-faq-and-rules-addon.zip -d extras`

becomes:

`unzip /var/www/mytheme-store-faq-and-rules-addon.zip -d extras`
{% endhint %}

```bash
cd /var/www/tebex-store/theme
mkdir -p extras
unzip /var/www/<theme>-store-faq-and-rules-addon.zip -d extras
rm /var/www/<theme>-store-faq-and-rules-addon.zip
chown -R www-data:www-data /var/www/tebex-store/theme/extras
systemctl restart tebex-store
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Checking the add-on

1. Sign in to your admin panel at `https://store.example.com/admin/login`.
2. Open <mark style="color:$primary;">**Add-ons**</mark> and click the add-on, for example **FAQ & Rules**.
3. It must say <mark style="color:$primary;">**Add-on installed**</mark>.

<details>

<summary>It doesn't say "Add-on installed"</summary>

* Check that the folder is directly inside `theme/extras`, for example `theme/extras/faq-and-rules`, and not one folder deeper.
* Make sure you restarted the website after uploading.

</details>
{% endstep %}

{% step %}
### Setting up the add-on

Each add-on has its own settings tab in the admin panel.

{% tabs %}
{% tab title="Rank Table" %}
1. Pick your **rank category** from the list.
2. Fill in the **Features** table on the same tab.
{% endtab %}

{% tab title="Gift Cards" %}
1. Pick your **gift card category** from the list.
2. Choose the packages for the **amount** and **premium** slots.
{% endtab %}

{% tab title="Pages" %}
For the **Patron**, **Vote**, **FAQ**, **Rules** and **Staff** pages:

1. Create a page in Tebex here: <https://creator.tebex.io/pages>.
2. Give it a title that matches the add-on's **page title** setting exactly.
3. Turn the page on in the add-on's tab.

{% hint style="warning" %}
The title is case sensitive: `Vote` and `vote` are not the same.
{% endhint %}
{% endtab %}

{% tab title="Upselling & Coin Slider" %}
1. Turn it on.
2. For each slot, set the **parent package**, the **packages** and the **amounts**.
{% endtab %}
{% endtabs %}
{% endstep %}
{% endstepper %}

***

### Removing an add-on

Delete the add-on's folder from <kbd>theme/extras</kbd> and restart the website: press <mark style="color:$primary;">**Restart**</mark> on the Node.js app page, or run `systemctl restart tebex-store` on a VPS.
