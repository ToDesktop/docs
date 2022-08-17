# 💄 Add Custom CSS to your Desktop App

We add a `todesktop` class to the html element on each page of your app. You can use this to identify when your app is being run as a desktop app.

### Hide element from desktop app

If you want to hide an element on your desktop app you could do something like this:

{% tabs %}
{% tab title="app.css" %}
```css
.announcement {
  background-color: hotpink;
  /* other styles... */
}

html.todesktop .announcement {
  display: none;
}
```
{% endtab %}

{% tab title="index.html" %}
```markup
<body>
  <div class="announcement">
    You should download our desktop app!
  </div>
  <!-- rest of your app -->
</body>
```
{% endtab %}
{% endtabs %}

### Show element on desktop app only (hide from web app)

You can also do the opposite and only show an element in your desktop app.

A common use-case is to show browser controls (back, forward, refresh) in your desktop app's user interface. Here's an example of how you could achieve this:

{% tabs %}
{% tab title="app.css" %}
```css
.back-button, .forward-button {
  display: none;
}

html.todesktop .back-button,
html.todesktop .forward-button {
  display: block;
}
```
{% endtab %}

{% tab title="index.html" %}
```markup
<nav>
  <a href="/">Home</a>
  <a class="back-button" onclick="window.history.back()">←</a>
  <a class="foward-button" onclick="window.history.forward()">→</a>
</nav>
```
{% endtab %}
{% endtabs %}

### Platform-specific CSS

You may wish to add styles that apply only on specific operating systems.

| Class name                   | Platform (operating system) target |
| ---------------------------- | ---------------------------------- |
| `.todesktop-platform-win32`  | Windows                            |
| `.todesktop-platform-darwin` | macOs                              |
| `.todesktop-platform-linux`  | Linux                              |

In the styles below we add a margin that will only apply on the Mac operating system.

```css
html.todesktop-platform-darwin .header {
  margin-top: 10px;
}
```

