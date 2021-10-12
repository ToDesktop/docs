# 🗺 Window

## todesktop.window.minimize

Minimize the currently active window

```
  window.todesktop.window.minimize()
```

## todesktop.window.maximize

Maximize the currently active window

```
  window.todesktop.window.maximize()
```

## todesktop.window.unmaximize

Unmaximizes the currently active window

```
  window.todesktop.window.unmaximize()
```

## todesktop.window.fullscreen

Sets the currently active window to fullscreen

```
  window.todesktop.window.fullscreen()
```

## todesktop.window.unfullscreen

Unsets the currently active window to fullscreen

```
  window.todesktop.window.unfullscreen()
```

## Window event listeners

#### Entered fullscreen mode

```javascript
window.todesktop.on('window.enter-full-screen', () => {
    console.log('window is now in fullscreen mode')
});
```

#### Exit fullscreen mode

```javascript
window.todesktop.on('window.leave-full-screen', () => {
    console.log('window has left fullscreen mode')
});
```
