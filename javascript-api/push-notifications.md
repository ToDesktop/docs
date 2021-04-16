---
description: Push notifications through Firebase Cloud Messaging
---

# 👉 Push Notifications

{% hint style="info" %}
Push notifications are not enabled by default for all apps. If you want us to enable them in your app then email us at hi@todesktop.com.
{% endhint %}

## todesktop.pushNotifications.start

To start the push notifications service all you need is a sender ID.

```javascript
  window.todesktop.pushNotifications.start("12345678901")
```

## todesktop.on\('pushNotifications.start'\)

Triggered when the push notifications service is started successfully and an FCM registration token has been received.

```javascript
window.todesktop.on('pushNotifications.start', (e, token) => {
    console.log(`Your FCM token is: ${token}`)
});
```

## todesktop.on\('pushNotifications.receive'\)

Triggered when a push notifications service is received.

```javascript
window.todesktop.on('pushNotifications.receive', (e, notification) => {
  console.log(notification)
  /**
  * {
	* 	"from": "14017693762",
	* 	"priority": "normal",
	* 	"notification": {
	* 		"title": "Hello World",
	* 		"body": "FooBar"
	* 	},
	* 	"collapse_key": "do_not_collapse"
	* }
  **/
});
```

## todesktop.on\('pushNotifications.error'\)

Triggered when the push notifications service is started successfully and an FCM registration token has been received.

```javascript
window.todesktop.on('pushNotifications.error', (e, error) => {
  // Notify user of error
});
```

## todesktop.on\('pushNotifications.tokenUpdate'\)

Triggered when the FCM registration token has been updated.

```javascript
window.todesktop.on('pushNotifications.tokenUpdate', (e, token) => {
    console.log(`Your FCM token has been updated to: ${token}`)
});
```

