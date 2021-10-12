# 🖱 Make a Transparent Titlebar Draggable (macOS only)

By default, a tranparent title bar is not draggable, you will need to add some CSS styles to your site to make the window draggable.

You can give an element the ability to **drag** the window by using`-webkit-app-region: drag` in css.

If you want certain elements marked as **non-draggable** then you can use`-webkit-app-region: no-drag`So, you might end up doing something like this:

```css
html.todesktop .header {
  -webkit-app-region: drag;
}

html.todesktop .header .nav {
  -webkit-app-region: no-drag;
}
```

The `html.todesktop` class pre-selector will ensure that the css is only applied when running as a desktop app. You can learn more about this here:

{% content-ref url="adding-custom-css-to-your-desktop-app.md" %}
[adding-custom-css-to-your-desktop-app.md](adding-custom-css-to-your-desktop-app.md)
{% endcontent-ref %}
