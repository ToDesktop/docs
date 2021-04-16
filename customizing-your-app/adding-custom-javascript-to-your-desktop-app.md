# 👩‍💻 Add Custom Javascript to your Desktop App

We expose a `window.todesktop` object which provides info about the device and the app as well as methods which provide extra features.

You can use the presence of this object to add different behaviour to your app when it is running as a desktop app.

```javascript
if (window.todesktop) {
  alert('You are running as a desktop app.');
}
```

{% hint style="info" %}
We use the most up to date version of Chromium so you can use the latest browser features when your app is running as a desktop app.
{% endhint %}

We recommend separating all of your desktop specific logic into a separate javascript file:

{% page-ref page="../recipes/separating-desktop-logic.md" %}

You can see all of the available info and methods on the `window.todesktop` object in that section of the docs.

{% page-ref page="../javascript-api/introduction.md" %}

