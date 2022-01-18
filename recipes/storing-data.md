# 💾 Storing Data

A common pattern in SaaS apps is to give each customer a unique subdomain. By default second-level domains are considered internal to your application. (For more info see _Defining Internal URLs_ below)

{% content-ref url="../app-options/defining-internal-urls.md" %}
[defining-internal-urls.md](../app-options/defining-internal-urls.md)
{% endcontent-ref %}

Say you have your customers login at https://login.yourapp.com which then redirects them to https://yourcustomer.yourapp.com. You can store the last used subdomain and redirect your users there when they open the app.

```javascript
// On login to subdomain https://yourcustomer.yourapp.com
if (window.todesktop) {
  localStorage.setItem('subdomain', 'yourcustomer');
}

// When not already on subdomain then redirect to last used subdomain
if (window.todesktop) {
  const subdomain = localStorage.getItem('subdomain')

  if (subdomain) {
    window.location = `https://${subdomain}.yourapp.com`
  }
}
```



{% hint style="info" %}
We recommend having a separate javascript app for all of your ToDesktop specific login and importing that conditionally when your app is running as a desktop app.
{% endhint %}

