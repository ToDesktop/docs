---
description: >-
  A context menu pops up where the mouse cursor is to provide easily accessible
  actions. Usually, it is used when you right-click on an item.
---

# 🎚 Context menu

### Create a context menu

`window.todesktop.contextMenu.create(menuTemplate)`

* `menuTemplate` Array of objects - For full documentation refer to [Electron's documentation about the `options` object in the MenuItem constructor](https://www.electronjs.org/docs/api/menu-item#new-menuitemoptions).

For example, to create a context menu like the screenshot below:

![](../.gitbook/assets/image%20%2818%29.png)

You would use the following code:

```javascript
window.todesktop.contextMenu.create([
    {
      label: "Log 'hi'",
      click: () => {
        console.log("hi");
      },
    },
    { role: "reload" },
    { type: "separator" },
    { role: "togglefullscreen" },
  ]);
```

### Create a right-click context menu

Usually, you will want to provide a context menu when a user right-clicks on something in your app. To do this you will want to prevent the default action of the `contextmenu` event.

#### Example: Add a custom emoji picker when right-clicking on a textarea

First, let's make sure that we have a `textarea` on the page.

```markup
<textarea id="my-message" cols="60" rows="10"></textarea>
```

Next, let's listen for `contextmenu` events on the `textarea` element and provide our own custom context menu instead.

```javascript
document.getElementById("my-message").addEventListener("contextmenu", (e) => {
  // Prevent the usual context menu from appearing
  e.preventDefault();
  
  // Show our custom context menu instead
  window.todesktop.contextMenu.create([
    {
      label: "Add Emoji",
      click: () => {
        // In this case, you would provide the `showEmojiPanel` function
        showEmojiPanel();
      },
    },
    { type: "separator" },
    { role: "copy" },
    { role: "paste" },
  ]);
});

```

![](../.gitbook/assets/image%20%2817%29.png)

