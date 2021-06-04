# ℹ️ Info

We provide helpful information via the `window.todesktop` object. Here is an overview of what's available:

```javascript
if (window.todesktop) {
  /*
    The current version of your app: e.g. '1.0.0'
  */
  console.log(window.todesktop.version);
  
  /*
    The current version of Electron: e.g. '7.1.2'
  */
  console.log(window.todesktop.electronVersion);
  
  /*
    Same as os.platform() in node: e.g. 'darwin'
  */
  console.log(window.todesktop.os.platform);

  /*
    Same as os.release() in node: e.g. '18.6.0'
  */
  console.log(window.todesktop.os.release);
  
  /*
    Same as os.type() in node: e.g. 'Darwin'
  */
  console.log(window.todesktop.os.type);
    
  /*
    Same as os.arch() in node: e.g. 'x64'
  */
  console.log(window.todesktop.os.arch);
}
```

{% hint style="info" %}
Always make sure `window.todesktop` is present before trying to access its properties or use its methods.
{% endhint %}

