##NOV 19, 2015
###       JQuery snippets

#### Event Fired When Checkbox State Modified (after v1.6)
```javascript
    $(document).ready(function() {
        $("#IdOfCheckbox").change(function() {
            if ($(this).prop("checked")) {
                // do when change from unchecked to checked
            } else {
                // do when change from checked to unchecked
            }
        });
    });
	```