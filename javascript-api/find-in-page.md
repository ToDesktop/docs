---
description: Integrate native web "find in page" feature
---

# 👀 Find In Page

## todesktop.contents.findInPage.start\(text, options\)

To start the find in page feature, all you need is specify a text \(string\).

```javascript
todesktop.contents.findInPage.start(text)
```

You can also configure the experience using these `options`:

* `forward` Boolean \(optional\) - Whether to search forward or backward, defaults to `true`
* `findNext` Boolean \(optional\) - Whether the operation is first request or a follow up, defaults to `false`
* `matchCase` Boolean \(optional\) - Whether search should be case-sensitive, defaults to `false`

For example, to find text backward:

```javascript
todesktop.contents.findInPage.start(text, { forward: false })
```

## todesktop.contents.findInPage.stop\(\)

Stop find in page

## todesktop.on\("found-in-page", eventHandler\)

You can also listen to the event `found-in-page` to update your UI accordingly when the find in page feature is being used.

```javascript
window.todesktop.on("found-in-page", (event, result) => {
  // ...
})
```

* `event` Event
* `result` Object
  * `requestId` Integer
  * `activeMatchOrdinal` Integer - Position of the active match.
  * `matches` Integer - Number of Matches.
  * `selectionArea` Rectangle - Coordinates of first match region.
  * `finalUpdate` Boolean

