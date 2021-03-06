# .closestDescendant( selector [, findAll] )

Breadth first search for the selector downward in the DOM tree.

## Getting Started
Download the minified version [dist/closestDescendant.min.js][min] or the uncompressed version 
[dist/closestDescendant.js][max] and load or add it in your page.

[min]: https://raw.github.com/tlindig/jquery-closest-descendant/master/dist/closestDescendant.min.js
[max]: https://raw.github.com/tlindig/jquery-closest-descendant/master/dist/closestDescendant.js

Or add this links to get jQuery and the plugin online without download:

```html
<script src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
<script src="https://github.com/tlindig/jquery-closest-descendant/raw/master/dist/closestDescendant.min.js"></script>
```

After this, you can call this method on every jQuery wrapped DOM element.

```html
<script>
jQuery(function($) {
  // ...	
  var closestSub = $('#elem').closestDescendant('.mySubItem');
  // ...
});
</script>
```

## Documentation

Get the first element(s) that matches the selector by traversing down through its descendants in the DOM tree level by level. It use a breadth first search (BFS), that mean it will going deeper in a subtree only until the first matching descendant was found in the current subtree.

Different to the .find() is, that it will return only the first match element in a subtree.

Parameter: {selectors} **selector** *-required-* a jQuery selector

Parameter: {boolean} **findAll** *-optional-* default is false, so tree walking will be stopped at fist match. If true, every subtree will be visited to find one match.

Returns: {jQuery} jQuery object with the matched element(s). If did not found one, an empty jQuery object (.length === 0) will be returned.

## Demo

 Here you can see the plugin in action: [Demo][demo]
 [demo]: http://tlindig.github.io/jquery-closest-descendant/

## Example

```html
	<div id="start">
		<div>
			<div>
				<div id="e1" class="c">
					e1
				</div>
			</div>
		</div>
		<div id="e2" class="c">
			e2
		</div>
		<div id="e3" class="c">
			e3
			<div id="e4" class="c">
				child of e3
			</div>
		</div>
	</div>
```

```javascript
jQuery('#start').closestDescendant(".c")
```
result: #e2

in contrast the `find`-method:

```javascript
jQuery('#start').find(".c:first")
```
result: #e1


```javascript
jQuery('#start').closestDescendant(".c", true)
```
result: #e2, #e3, #e1

in contrast the `find`-method:

```javascript
jQuery('#start').find('.c')
```
result: #e1, #e2, #e3, #e4

## History

Befor the [jQuery Plugin Database crashed] [crashed], I published this plugin under the name "closestChild". 
You can view the old source here:  [closestChild][oldSource]
[crashed]:http://blog.jquery.com/2011/12/13/plugins-site-update-the-old-is-new-again/
[oldSource]: https://github.com/groe/nested_form/commit/c5e9f0e5290cc3989978b14d29742bb116eb57a1



