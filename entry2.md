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
    
#### Button that posts data to controller and then displays icon to show complete
```razor
<div class="col-lg-3">
    @if (!@Model.Checked)
    {
        <input type="button" id='btnMark-@(Model.Id)' class="btn" value="Mark as Checked" />
        <button type="button" class="btn btn-default" aria-label="Left Align" style="display: none;" id="btn-ok-@(Model.Id)">
            <span class="glyphicon glyphicon-ok" aria-hidden="true" ></span>
        </button>
    }
    <script type="text/javascript">
        $(function () {
            $('#btnMark-@(Model.Id)').click(function () {
                $.post("/Home/Mark", { guid: "@(Model.Id)" })
                    .done(function (data) {                                
                        $('#btn-ok-@(Model.Id)').show();
                    });
            });
        });
    </script>
</div>    
    