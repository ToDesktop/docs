---
description: >-
  The Application menu lives at the top of the screen on Mac. On Windows, you
  can find it under your app window's title bar. You can easily add items to
  this menu using our Application Menu API.
---

# 🎛 Application Menu

{% hint style="warning" %}
This API is in beta and may change (or be completely removed) without warning.
{% endhint %}

### Add a menu item to the application menu

`window.todesktop.appMenu.add(parentMenu, label, callback, [options])`

**Promise\<void> **-** **Menu Item is added to the application menu model. However, it will not appear on the UI until `refresh()` is called.

This allows you to easily add custom items to the application menu that control your application. 

{% hint style="info" %}
The items you add to the application menu will not appear on the UI until you call `window.todesktop.appMenu.refresh().`
{% endhint %}

```javascript
const parentMenu = 'File'
const label = 'Save Note'
const options = {
  // "accelerator" is the keyboard shortcut that you can use
  // to trigger the menu item 
  accelerator: 'CommandOrControl+S'
}

await window.todesktop.appMenu.add(
  parentMenu,
  label,
  () => {
    // Put your app logic to "save a note" here
  },
  options
)

// This is required for the additional items to appear in the UI
await window.todesktop.appMenu.refresh()
```

!["Save Note" has been added to the Application Menu on Mac](<../.gitbook/assets/image (15).png>)

### Refresh the application menu to reflect any changes

`window.todesktop.appMenu.refresh()`

**Promise\<void> **-** **The application menu is refreshed and the UI has been updated.

When you add a menu item to the menubar, it does not immediately appear in the application menu. You need to call `refresh()` to update the menu that is displayed on the UI.

If you are adding multiple items to the application menu then it is best to only call `refresh()` _after _you have added all of the necessary items to the application menu.

```javascript
// Batch add all the app menu items
await Promise.all([
  window.todesktop.appMenu.add(
    // ...
  ),
 window.todesktop.appMenu.add(
    // ...
  ),
 window.todesktop.appMenu.add(
    // ...
  )
])

// Once they are all added then you can call refresh
await window.todesktop.appMenu.refresh()
```

