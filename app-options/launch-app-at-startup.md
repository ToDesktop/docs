# 🚀 Launch at Startup (macOS, Windows only)

## What is Launch at Startup?

This option lets you specify whether your desktop app should launch when a user starts their computer.

By default, this is disabled for **Desktop** apps and enabled for **Menubar** apps.



### Enabling Launch at Startup

In your Edit app page, simply check the _Launch at Startup By Default_ checkbox under _App Options:_

![App Options panel for toggling Launch at Startup by Default](<../.gitbook/assets/Launch app at startup.png>)

If enabled, your desktop app will now launch by default when a user starts up their computer.

{% hint style="info" %}
Your users will always have an option to toggle this setting on or off in their native app menus (application menu and menubar/tray menu).
{% endhint %}



## Using the Javascript API

We expose a `launchSettings`  object and two helper methods if you wish to add custom logic to your app. 

#### Get Launch Settings

`window.todesktop.app.getLaunchSettings()` returns a promise which resolves to a  `launchSettings`  object. This object has the following attributes:

| Attribute           | Type    | Description                                                  |
| ------------------- | ------- | ------------------------------------------------------------ |
| willLaunchAtStartup | boolean | The user's current setting for launching the app at startup. |

```javascript
const launchSettings = await window.todesktop.app.getLaunchSettings()

console.log(launchSettings);
//  { 
//    willLaunchAtStartup: true
//  }
```

####

#### Set Launch Settings

`window.todesktop.app.setLaunchSettings(launchSettings)` allows you to update a user's launch settings.

```javascript
/*
 sets the value of willLaunchAtStartup to true
*/

window.todesktop.app.setLaunchSettings({
  willLaunchAtStartup: true
})
```

####

#### Full example

The following is an example of how to toggle the status of _Launch _at _Startup _if a user clicks on a button.

```javascript
button.addEventListener('click', () => {

  // Gets the launch settings object
  const { willLaunchAtStartup } = await window.todesktop.app.getLaunchSettings()
  
  // toggles the value of will launch at startup
  window.todesktop.app.setLaunchSettings({
    willLaunchAtStartup: !willLaunchAtStartup
  })
})
    
```



You can learn more about our JavaScript API through the link below:

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}
