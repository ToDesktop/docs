# ☁ Download Links for your Website

When linking to your desktop app you can use our **universal** link. You can add this link to your website and it will work regardless of which operating system your user is running.

The universal link will:

* **Detect the operating system** and deliver the correct installer:
  * Windows: `NSIS` if enabled, otherwise it will fall back to `MSI`, or `AppX`
  * Mac: `DMG` if enabled, otherwise it will fall back to `ZIP`.
  * Linux: `AppImage` if enabled, otherwise it will fall back to `Debian`, `RPM`, or `Snap Store`.
* Always deliver the **latest version** of your desktop app.  So if you publish a new version in the future then you don't need to update the link.

Your universal link looks like this:

```
https://dl.todesktop.com/{{YOUR_APP_ID}}
```

You can get your universal link from the ToDesktop builder, just click on the cog in top-right.

![](<../.gitbook/assets/copy universal link to clipboard.png>)

Once you click the menu item then the Universal URL will be copied to your clipboard. The universal download link should look something like this:

```
https://dl.todesktop.com/190911i1k98bqno
```

If you want to use the URL for the Mac/Windows/Linux build then you can click the menu item for those URLs instead. Platform specific download links look like this:

* Windows: `https://dl.todesktop.com/{{YOUR_APP_ID}}/windows`
* Mac: `https://dl.todesktop.com/{{YOUR_APP_ID}}/mac`
* Linux: `https://dl.todesktop.com/{{YOUR_APP_ID}}/linux`

So, if you want to get the latest Mac build of your desktop app then your download link should look something like this:

```
https://dl.todesktop.com/190911i1k98bqno/mac
```

To add a simple download link to your website, you could use the following HTML:

```markup
<!-- Detect user's operating system -->
<a href="https://dl.todesktop.com/190911i1k98bqno" download>
  Download our Desktop App
</a>

<!-- Mac -->
<a href="https://dl.todesktop.com/190911i1k98bqno/mac" download>
  Download our Mac App
</a>

<!-- Windows -->
<a href="https://dl.todesktop.com/190911i1k98bqno/windows" download>
  Download our Windows App
</a>

<!-- Linux -->
<a href="https://dl.todesktop.com/190911i1k98bqno/linux" download>
  Download our Linux App
</a>
```
