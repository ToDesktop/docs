# 👀 Add Find In Page to your Desktop App

ToDesktop supports the native "find in page" feature you normally use in web browsers. ToDesktop provides the APIs you will need to implement the UI in your desktop app.

### HTML

First up let's add some simple HTML (or JSX) for the input box (to get the text we want to look for) and buttons to start (& navigate) the search and to stop it. We also need to display the current match ordinal and the total number of matches.

{% tabs %}
{% tab title="HTML" %}
```markup
<div class="find-in-page">
  <input class="find-in-page-input"></input>
  <button class="find-in-page-find-forward">
    ▶
  </button>
  <button class="find-in-page-find-backward">
    ◀
  </button>
  <button class="find-in-page-stop">
    ⏹️
  </button>
  <p>
    <span class="find-in-page-active-match-ordinal">
      0
    </span>
    <span>/</span>
    <span class="find-in-page-matches">
      0
    </span>
  </p>
</div>
```
{% endtab %}

{% tab title="JSX" %}
```jsx
{
  // Only render this HTML if we are in the desktop app
  window.todesktop &&
  (
    <div className="find-in-page">
      <input className="find-in-page-input" />
      <button className="find-in-page-find-forward">
        ▶
      </button>
      <button className="find-in-page-find-backward">
        ◀
      </button>
      <button className="find-in-page-stop">
        ⏹️
      </button>
      <p>
        <span className="find-in-page-active-match-ordinal">
          0
        </span>
        <span>/</span>
        <span className="find-in-page-matches">
          0
        </span>
      </p>
    </div>
  )
}
```
{% endtab %}
{% endtabs %}

### Making it work

Now let's make our buttons actually work. We can use ToDesktop's `findInPage.find()` and `findInPage.stop()` methods to start and stop the search.

We also need to listen to the `found-in-page` event to update the current match ordinal and the total number of matches in the UI accordingly.

```javascript
if (window.todesktop) {
  // This block is only executed when running as a desktop app
  
  const findForwardBtn =
    document.querySelector(".find-in-page-find-forward");
  const findBackwardBtn =
    document.querySelector(".find-in-page-find-backward");
  const stopBtn =
    document.querySelector(".find-in-page-stop");
  const input = 
    document.querySelector(".find-in-page-input");
  const activeMatchOrdinalSpan = 
    document.querySelector(".find-in-page-active-match-ordinal");
  const matchesSpan = 
    document.querySelector(".find-in-page-matches");

  findForwardBtn.addEventListener("click", () => {
    // Find forward
    const text = input.value;
    window.todesktop.contents.findInPage.find(text);
  });
  
  findBackwardBtn.addEventListener("click", () => {
    // Find forward from the current position
    const text = input.value;
    window.todesktop.contents.findInPage.find(text, { forward: false });
  });
  
  stopBtn.addEventListener("click", () => {
    // Stop the search
    window.todesktop.contents.findInPage.stop();
  });
  
  // listen to when find in page feature is being used
  // and update the UI accordingly
  todesktop.on("found-in-page", (event, result) => {
    const { activeMatchOrdinal, matches } = result;
    activeMatchOrdinalSpan.innerText = activeMatchOrdinal;
    matchesSpan.innerText = matches;
  });
}
```

