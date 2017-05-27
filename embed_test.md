```
<div class="leaderboard-widget">
<div id="widget-root"></div>
<script type="text/javascript" id="embed-me-31415" class="embed-me-31415">
	  (function() {
	    function async_load(){
	      var s = document.createElement('script');
	      s.type = 'text/javascript';
	      s.async = true;
	      var theUrl = 'http://159.203.77.70:3000/widget.js';
	      s.src = theUrl + ( theUrl.indexOf("?") >= 0 ? "&" : "?") + 'ref=' + encodeURIComponent(window.location.href);
	      var embedder = document.getElementById('embed-me-31415');
	      embedder.parentNode.insertBefore(s, embedder);
	    }
	    if (window.attachEvent)
	      window.attachEvent('onload', async_load);
	    else
	      window.addEventListener('load', async_load, false);
	  })();
	</script>

		<script src='https://unpkg.com/axios/dist/axios.min.js'></script>
		<script src='https://cdnjs.cloudflare.com/ajax/libs/react/15.4.2/react.min.js'></script>
		<script src='https://cdnjs.cloudflare.com/ajax/libs/react/15.4.2/react-dom.min.js'></script>
</div>
```