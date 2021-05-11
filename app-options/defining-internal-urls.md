# 🔗 Defining Internal URLs

### What are Internal URLs?

Internal URLs are links that open within your desktop app window instead of an external browser window i.e. Chrome, Safari, Firefox etc.

{% hint style="info" %}
If you want to force a page to open in the user's browser then you can use our [`openUrlInBrowser` API](../javascript-api/navigation.md#open-a-url-in-the-users-default-browser).
{% endhint %}

By default, login provider URLs \(also known as [OAuth](https://en.wikipedia.org/wiki/OAuth)\) and URLs on the same domain as your app are considered internal.

Here is an example of some links considered internal and external if your web app is `https://www.icecream.com`**:**

| Internal URLs | External URLs |
| :--- | :--- |
| ✅ `https://app.icecream.com` | ❌ `https://apple.com` |
| ✅ `https://sundaes.icecream.com` | ❌ `https://amazon.com` |
| ✅ `https://accounts.google.com/oauth` |  |

{% hint style="info" %}
Login providers currently supported include: Facebook, LinkedIn, Github, Twitter and Google.
{% endhint %}

### Adding Internal URLs

You can add more internal URLs if needed. 

In your Edit app page, select the _Internal URLs_ checkbox under _App Options_. Here you can add a regex \(short for regular expression\) of URLs to be considered internal.

For example, if your app is `https://www.icecream.com` and you want to include the domains of `apple.com` and `amazon.com` as internal, this is how the regex input would look:

```text
.*(apple.com|amazon.com).*
```

Configuring this correctly can be tricky so if you have any trouble please get in touch and we will help you out.

![Editing Internal URLs on the Edit App page](../.gitbook/assets/image%20%283%29.png)

### Dynamically adding Internal URLs

Sometimes it may be neccesary to dynamically change internal URLs. You can use our runtime API to do this. To get current internal URLs you can use `window.todesktop.app.getInternalUrls()`. To update internal URLs you can use `window.todesktop.app.updateInternalUrls(newInternalUrls)`.

```javascript
await window.todesktop.app.getInternalUrls();
// -> ".*(apple.com|amazon.com).*"

// Let's add google.com as an internal URL
const newInternalUrls = ".*(apple.com|amazon.com|google.com).*";
await window.todesktop.app.updateInternalUrls(newInternalUrls);

await window.todesktop.app.getInternalUrls();
// -> ".*(apple.com|amazon.com|google.com).*"
```

