```
<div id="container"/>
<script>
  var button = document.createElement('button');
  var textNode = document.createTextNode('Click Me!');
  button.appendChild(textNode);
  button.className = 'mdl-button mdl-js-button mdl-js-ripple-effect';
  componentHandler.upgradeElement(button);
  document.getElementById('container').appendChild(button);
</script>
```


```
<!-- Accent-colored raised button with ripple -->
<button class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect mdl-button--accent">
  Button
</button>
<!-- Colored FAB button -->
<button class="mdl-button mdl-js-button mdl-button--fab mdl-button--colored">
  <i class="material-icons">add</i>
</button>

```



```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```


