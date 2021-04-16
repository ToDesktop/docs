# 🖥 Separate Desktop Logic from Web App Logic

We recommend adding all of your custom javascript into a separate file and importing it when your app is being run as a desktop app. Here's how to do this:

```markup
<script type="module">
  if (window.todesktop) {
    import('some-module.mjs');
  }
</script>
```

{% hint style="info" %}
Because your desktop app will always be running a very recent version of Chromium, you can rely on the latest browser features being present when your app is running as a desktop app.
{% endhint %}



