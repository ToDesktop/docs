---
description: How to use custom protocol links to launch your app built with ToDesktop.
---

# ⛓ App Protocols and Deeplinks

## What are App Protocols?

You've probably seen app protocols before. Perhaps you've seen them with iTunes (`itmss://`) or Spotify (`spotify://`) or Slack (`slack://`). App protocols provide an easy way for you to launch your application from inside another application. 

One common use-cases is to launch a desktop application from a website.

```markup
<a href="spotify://">Open Spotify App</a>
```

### What are Deeplinks?

We can also add more information to go to a specific part of a desktop application. We call this a ‘deeplink’.

```markup
<a href="spotify://track:1mIBixqmt8vbDNXiKqLTGJ">
  Play “Broken Together” by “Mani Obeya” on Spotify
</a>
```

## App Protocols and ToDesktop

### Enabling App Protocols

You can enable App Protocols for your app by selecting the “Support App Protocol (deeplink)” option in the “App Options” box. You can then type the App Protocol that you wish to use. In the example below, we have chosen `interplay://` as the app protocol.

![](<../.gitbook/assets/app protocols (1).png>)

### Using App Protocols

Let's use the app protocol of `interplay://` in our examples below.

#### Simple App Protocol

**`interplay://` → `https://app.interplay.io`**

This will open Interplay app at the default location. If the app is already opened then the window will gain focus.

#### Deeplink

**`interplay://foo/bar` → `https://app.interplay.io/foo/bar`**

Deeplinks allow you to specify a path to navigate to in your app. This will open Interplay app at the `foo/bar` path.

**Example**

So, if you wanted to link from a website to a deeplink within Interplay app then you could do something like this:

```markup
<a href="interplay://foo/bar">Open FooBar on Interplay app</a>
```

### Manually handling App Protocols

You may wish to opt-out of the default behaviour for App Protocols. For example, you may wish to pass data to your app through a URL but not load a new page.

Let's say that we want to handle the URL `spotify://pause`. When this link is opened we want to pause the music but we don't want to change the current URL of our app. We can prevent navigation by calling `event.preventDefault()`. Here's an example:

```javascript
window.todesktop.on("open-protocol-url", (_, event) => {
  /*
  * If URL contains 'pause' then prevent navigation
  * and pause the audio player.
  */
  if (event.url.includes("pause")) {
    event.preventDefault();
    audio.pause();
  }
});
```

## Video

{% embed url="https://vimeo.com/359512123" %}

### AppImage Support

Your users should use [AppImageLauncher](https://github.com/TheAssassin/AppImageLauncher) to install and integrate your app into their desktop environment. Otherwise this feature may not work.
