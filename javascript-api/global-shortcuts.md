---
description: >-
  We allow you to register global keyboard shortcuts that work when your app
  doesn't have keyboard focus.
---

# ⌨ Global Shortcuts

## Accelerators

See [https://www.electronjs.org/docs/api/accelerator](https://www.electronjs.org/docs/api/accelerator) for how to define accelerators

## todesktop.shortcut.isRegistered(accelerator)

**Promise\<Boolean> **-** **Whether your application has registered the accelerator (shortcut). 

Note if another application has taken the accelerator this will still return `false`

```javascript
await todesktop.shortcut.isRegistered("Command+G")
```

## todesktop.shortcut.register(accelerator, callback)

**Promise\<Boolean> - **Whether the shortcut was registered successfully. 

Registers the global shortcut of `accelerator`. The callback is called when the user presses the shortcut. 

Note when the accelerator is already taken by other applications, this call will silently fail.

```javascript
todesktop.shortcut.register("Command+G", () => {
    console.log("The shortcut was pressed");
});
```

## todesktop.shortcut.unregister(accelerator)

**Promise\<Boolean> **- Whether the shortcut was successfully unregistered

Unregisters the global shortcut of `accelerator`.

```javascript
todesktop.shortcut.unregister("Command+G");
```

## todesktop.shortcut.unregisterAll()

**Promise\<Boolean> ** - Whether all shortcuts were successfully removed

```javascript
todesktop.shortcut.unregisterAll();
```
