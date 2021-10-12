# 💗 Enlarging Menubar Window

## Your app at-a-glance

A menubar app is fantastic for providing a quick way to keep up to date with activity feeds, reports, or new content. Sometimes it can be a little restrictive because it's quite a small window into your app.

We provide an API that allows you to enlarge the menubar window which may make it easier to interact with your app and view more information.

{% embed url="https://vimeo.com/392547830" %}
Menubar app expanding video
{% endembed %}

### The API

#### Enlarge

 It's super simple. To enlarge the menubar window simply call:

```javascript
window.todesktop.menubar.enlarge();
```

By default, this will enlarge the window to a width of 800 and a height of 1000. Of course you can specify your own values if you like:

```javascript
window.todesktop.menubar.enlarge({ width: 1100, height: 600 });
```

#### Shrink

And to shrink the window back down to it's normal size, you can call `shrink()`:

```javascript
window.todesktop.menubar.shrink();
```

### Triggering the enlarge and shrink APIs

#### Keyboard shortcut

There are a number of ways that you can trigger the enlarge and shrink APIs. For example you could create a keyboard shortcut. In the example below we are enlarging the menubar window when the user presses shift + down, and we shrink the window when they press shift + up.

```javascript
// Set up a listener that triggers whenever a key is pressed
document.addEventListener('keydown', ({code, shiftKey}) => {
  if (code === 'ArrowDown' && shiftKey) {
    // Shift + down pressed simultaneously
    window.todesktop.menubar.enlarge();
  } else if (code === 'ArrowUp' && shiftKey) {
    // Shift + up pressed simultaneously
    window.todesktop.menubar.shrink();
  }
});
```

#### Clickable button

You may also want a clickable button on your UI which allows users to enlarge and shrink the UI. In the example below, we use the same button to toggle between enlarging and shrinking the window.

```javascript
// First, get a reference to our button in the DOM
const toggleEnlargeButton = document.querySelector('.toggle-button');

// Next, store the resize state of the menubar.
// By default the menubar isn't enlarged
let isEnlarged = false;

// Set up a listener that triggers each time the button is clicked
toggleEnlargeButton.addEventListener('click', () => {
  if (isEnlarged) {
    // If window is enlarged then shrink it
    window.todesktop.window.menubar();
    isEnlarged = false;
  } else {
    // If window is *not* enlarged then enlarge it
    window.todesktop.window.menubar();
    isEnlarged = true;
  }
});
```

 
