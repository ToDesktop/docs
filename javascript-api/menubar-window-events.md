---
description: >-
  We include some event listeners that are specific to menubar. Allowing you to
  perform an action when a menubar is hidden or shown.
---

# 👂 Menubar Window Events

## todesktop.on\('show'\)

Triggered when a menubar window is shown.

```javascript
window.todesktop.on('show', () => {
    console.log('menubar window is now visible')
});
```

## todesktop.on\('hide'\)

Triggered when a menubar window is hidden.

```javascript
window.todesktop.on('hide', () => {
    console.log('menubar window is now hidden')
});
```

