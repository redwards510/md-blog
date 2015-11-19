##Nov 18 2015##
###Using XPath to scrape the web.###

[MSDN Reference](https://msdn.microsoft.com/en-us/library/ms256086%28v=vs.110%29.aspx)

[Example Page](http://www.amadorcourt.org/)

Imagine we want to match everything in the div with the class "hero2", but we didn't want to use that
class as our anchor (pretend we find it elsewhere and we only want this block). 

Put this in your JavaScript console:
`$x('//h4[contains(text(),"HOURS")]')`
You see that it only selects the H4 element. We want the descendents of it. This doesn't work either:
`$x('//h4[contains(text(),"HOURS")]/div')`

```html
<div class="simpleModule">            
	<h4>LOCATION AND HOURS OF OPERATION:</h4>
	<div class="hero2">   
		<!-- a bunch of text we want -->
	</div>   
</div>
```

We have to walk up from the H4 element and then we can select the DIV below it.
`//h4[contains(text(),"HOURS OF OPERATION")]/../div` 