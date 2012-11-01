#jQuery.pluginautoload
##Load debuggable Javascript scripts
Load a JavaScript file from the server using a GET HTTP request, then execute it. 
This function looklike jQuery.getScript() but it use LazyLoad system. So you can debug the loaded file with a Javascript debugger. 
With Firebug for exemple...

##Author
Marc Buils (marc.buils@marcbuils.fr)

##License
LGPL v3 (http://www.gnu.org/licenses/lgpl-3.0.txt)

##Current version
v0.1.0: 
 * Initial import

##Usation
For default use, load only jQuery.pluginautoload script:
```
$.loadScript( url [, callback()] )  
```
or
```
$.loadScript( url ).done( callback() );  
```
url: URL of the script to Load
callback: function without paraleters, called when the script is loaded.

This function return a jQuery.Deferred() object.

###Exemple 1: Exemple with Diferred (recommended)
```
<!doctype>
<html>
	<head>
		<meta charset="utf8"></meta>
		<title>Exemple of jQuery.loadScript with differed</title>
		<script src="http://code.jquery.com/jquery-1.8.2.min.js"></script>
		<script src="../jquery.loadscript.js"></script>
		<script>
			;(function($){
				$.loadScript('test.js').done(function(){
					$('#test').test();
				});
			})(jQuery);
		</script>
	</head>
	<body>
		<div id="test"></div>
	</body>
</html> 
```

###Exemple 2: Exemple with callback
```
<!doctype>
<html>
	<head>
		<meta charset="utf8"></meta>
		<title>Exemple of loadScript with callback</title>
		<script src="http://code.jquery.com/jquery-1.8.2.min.js"></script>
		<script src="../jquery.loadscript.js"></script>
		<script>
			;(function($){
				$.loadScript('test.js', function(){
					$('#test').test();
				});
			})(jQuery);
		</script>
	</head>
	<body>
		<div id="test">clique ici</div>
	</body>
</html>
```

###Exemple 3: Exemple multiple script loading
```
<!doctype>
<html>
	<head>
		<meta charset="utf8"></meta>
		<title>Exemple of multiple script loading</title>
		<script src="http://code.jquery.com/jquery-1.8.2.min.js"></script>
		<script src="../jquery.loadscript.js"></script>
		<script>
			;(function($){
				$.when( $.loadScript('test.js'), $.loadScript('test2.js') ).done(function(){
					$('#test').test();
					$('#test2').test2();
				});
			})(jQuery);
		</script>
	</head>
	<body>
		<div id="test">clique ici</div>
		<div id="test2">clique ici</div>
	</body>
</html>
```