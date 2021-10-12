# 🏷 App Icon Badging, Bouncing and Progress Bar

## Count Badges

{% hint style="info" %}
Works on **all platforms**
{% endhint %}

You can easily set the counter using the `setBadgeCount` method. Setting the count to `0` will hide the badge.

```javascript
window.todesktop.app.setBadgeCount(2);
```

![Badge count set to 2 (Mac)](<../.gitbook/assets/image (1).png>)

## Text Badges

{% hint style="info" %}
Works on **Mac** only
{% endhint %}

On mac, you have the option to set the set the dock badge to any text you like.

```javascript
window.todesktop.app.dock.setBadge("👋🙊 Hello");
```

![Text badge set to "👋🙊 Hello"](<../.gitbook/assets/image (2).png>)

## **Bouncing dock icon**

{% hint style="info" %}
Work on **Mac** only
{% endhint %}

Bouncing the dock icon has two modes: `critical` and `informational`. If no parameters are used then the default is `informational`.

* `informational` — the dock icon will bounce once (for a duration of one second)
* `critical` — the dock icon will bounce until either the application becomes active or the request is canceled

```javascript
// Bounce the dock icon once
window.todesktop.app.dock.bounce('informational');

// Bounce the dock icon for 5 seconds
const cancelBounceId = window.todesktop.app.dock.bounce('critical');
setTimeout(() => {
    window.todesktop.app.dock.cancelBounce(cancelBounceId);
}, 5000);
```

## Show progress bar

{% hint style="info" %}
Works on **all** platforms (Windows, Mac and Linux). On Linux, only the Unity desktop environment is supported.
{% endhint %}

```javascript
// Set progress bar to 75%
window.todesktop.window.setProgressBar(0.75)

// Set progress bar to intermediate mode. Any value
// greater than `1` will trigger intermediate mode
window.todesktop.window.setProgressBar(2)

// Remove progress bar. Any value less than `0`
// will remove the progress bar
window.todesktop.window.setProgressBar(-1)

// Set progress bar to 75% in error mode (Windows only)
window.todesktop.window.setProgressBar(0.75, {
    // Progress bar modes are only available on Windows.
    // Available modes are: 'indeterminate', 'error', and 'paused'.
    mode: 'error'
})
```

![Progress bar set to 0.75 (Mac)](<../.gitbook/assets/image (3).png>)

## Putting it all together — An homage to Daft Punk

We made a quick video that puts all the methods together. It's just a bit of fun and not very practical but we hope you enjoy it as much as we enjoyed making it (headphones recommended):

{% embed url="https://vimeo.com/356637449" %}

