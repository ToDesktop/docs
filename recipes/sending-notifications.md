# 🌟 Send Native Notifications

{% hint style="info" %}
Notifications are only available in secure contexts (HTTPS).
{% endhint %}

You can send notifications to your users with the [HTML5 Notifications API](https://developer.mozilla.org/en-US/docs/Web/API/Notifications_API). We intercept the notification and send a native OS notification to your user instead.

When sending a notification in a ToDesktop app is you do not have to request permission first with the `Notification.requestPermission()` method as you would in a web app.

If you only want to send notifications in your Desktop app you can check if the window.todesktop object is present:

```javascript
if (window.todesktop) {
  const notification = new Notification('Welcome to our desktop app.')
}
```

## Extra Features

ToDesktop also adds new features to HTML5 Notifications

## Custom sounds

You can specify a custom sound to be played when your notification is shown

```javascript
new Notification('Hello world', {
    sound: './notification.mp3',
})
```

