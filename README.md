# json-rendering-bookmarklet
Repo for my JSON prettier bookmarklet

See the transformation below:
[Screencast from 2023-11-21 16-58-21.webm](https://github.com/The-Best-Codes/json-rendering-bookmarklet/assets/106822363/6672af88-797f-4035-a850-b8f04ce2fff3)
<video src="https://github.com/The-Best-Codes/json-rendering-bookmarklet/assets/106822363/6672af88-797f-4035-a850-b8f04ce2fff3" controls autoplay></video>

Here is the code (url friendly):
```javascript
javascript:(function() { function syntaxHighlight(json) { json = JSON.stringify(json, undefined, 4); json = json.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;'); return json.replace(/("(\\u[a-zA-Z0-9]{4}|\\[^u]|[^\\"])*"(\s*:)?|\b(true|false|null)\b|-?\d+(?:\.\d*)?(?:[eE][+-]?\d+)?)/g, function (match) { var cls = %27color: black;%27; if (/^"/.test(match)) { if (/:$/.test(match)) { cls = %27color: green;%27; } else { cls = %27color: darkorange;%27; } } else if (/true|false/.test(match)) { cls = %27color: red;%27; } else if (/null|-?\d+(?:\.\d*)?(?:[eE][+-]?\d+)?/.test(match)) { cls = %27color: purple;%27; } return %27<span style="%27 + cls + %27">%27 + match + %27</span>%27; }); } var contentType = document.contentType; if (contentType === "application/json") { var json = JSON.parse(document.body.innerText); var highlighted = syntaxHighlight(json); document.body.innerHTML = %27<pre>%27 + highlighted + %27</pre>%27; document.body.style.fontFamily = "Arial, sans-serif"; document.body.style.fontSize = "15px"; } else { alert("This page does not contain JSON."); }}());
```
Here is the code (normal):
```javascript
javascript: (function () {
  function syntaxHighlight(json) {
    json = JSON.stringify(json, undefined, 4);
    json = json
      .replace(/&/g, "&amp;")
      .replace(/</g, "&lt;")
      .replace(/>/g, "&gt;");
    return json.replace(
      /("(\\u[a-zA-Z0-9]{4}|\\[^u]|[^\\"])*"(\s*:)?|\b(true|false|null)\b|-?\d+(?:\.\d*)?(?:[eE][+-]?\d+)?)/g,
      function (match) {
        var cls = "color: black;";
        if (/^"/.test(match)) {
          if (/:$/.test(match)) {
            cls = "color: green;";
          } else {
            cls = "color: darkorange;";
          }
        } else if (/true|false/.test(match)) {
          cls = "color: red;";
        } else if (/null|-?\d+(?:\.\d*)?(?:[eE][+-]?\d+)?/.test(match)) {
          cls = "color: purple;";
        }
        return '<span style="' + cls + '">' + match + "</span>";
      }
    );
  }
  var contentType = document.contentType;
  if (contentType === "application/json") {
    var json = JSON.parse(document.body.innerText);
    var highlighted = syntaxHighlight(json);
    document.body.innerHTML = "<pre>" + highlighted + "</pre>";
    document.body.style.fontFamily = "Arial, sans-serif";
    document.body.style.fontSize = "15px";
  } else {
    alert("This page does not contain JSON.");
  }
})();
```

To use the codes, create a new bookmark named "JSON" and set the URL to one of the above codes.
No credits or lisences.
