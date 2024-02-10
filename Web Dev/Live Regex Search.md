[[Bootcamp Notes]]
---
# Live Regex Search

```html
@section scripts {
<script src="https://code.jquery.com/jquery-3.7.1.js" integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"> </script> 
 <script>
    /// <summary>
    /// On each keypress, call search
    /// this performs a live searching function
    /// </summary>
    $(document).ready(function () {
        var delayTimer;
        var _baseURL = '@_baseURL';

    $("#searchQuery").on("input", function () {
            clearTimeout(delayTimer);

            var query = $(this).val(); 

            delayTimer = setTimeout(function () {
            $.ajax({
                url: _baseURL + "Clearances",
                type: "GET",
                data: { searchQuery: query },
                success: function (data) {
                    updateLiveSearchResults(data);
                },
                error: function (xhr, status, error) {
                }
            });
            }, 300); // Set a delay of 300 milliseconds (adjust as needed)
        });

        function updateLiveSearchResults(result) {
            var liveSearchResults = $("#liveSearchResults");
            liveSearchResults.empty(); 
            liveSearchResults.append(result);
        }
    });
</script>
}
```

in the controller

```csharp
public async Task<ActionResult> Index(string searchQuery) {

// rest of the code

	if (!string.IsNullOrEmpty(searchQuery))
	{
		clearances = clearances
			.Where(c => c.LastName.Contains(searchQuery, StringComparison.OrdinalIgnoreCase) || c.FirstName.Contains(searchQuery, StringComparison.OrdinalIgnoreCase));
	}

	// check if the page is sending an ajax request, then return _SearchResults
	if (Request.Headers["X-Requested-With"] == "XMLHttpRequest") 
	{
		return PartialView("_SearchResults", clearances);
	} 
}
```

in _SearchResults

```html
@model IEnumerable<NBI_MVC.Models.ClearanceViewModel>

@foreach (var item in Model)
{
    <tr>
        <td>@Html.DisplayFor(modelItem => item.Date)</td>
        <td>
            <div>
                <strong>Last Name:</strong> @Html.DisplayFor(modelItem => item.LastName)
            </div>
            <div>
                <strong>First Name:</strong> @Html.DisplayFor(modelItem => item.FirstName)
            </div>
        </td>
        <td>
            <div>
                <strong>Mobile Number:</strong> @Html.DisplayFor(modelItem => item.MobileNumber)
            </div>
            <div>
                <strong>Email Address:</strong> @Html.DisplayFor(modelItem => item.EmailAddress)
            </div>
        </td>
        <td>
            <td>
                <div>
                    <strong>@Html.DisplayNameFor(model => model.Branch): </strong>
                    @if (item != null && item.Branch != null)
                    {
                        @Html.DisplayFor(modelItem => item.Branch.BranchName)
                    }
                </div>
                <div>
                    <strong>Civil Status:</strong>
                    @if (item != null && item.CivilStatus != null)
                    {
                        @Html.DisplayFor(modelItem => item.CivilStatus.CivilStatusName)
                    }
                </div>
            </td>
        <td>
            <div class="container w-100">
                <img src="@item.ImageUrl" alt="image" class="userPhoto img-thumbnail" />
                <p>@item.ImageUrl</p>
            </div>
        </td>
        <td>
            <div class="btn-group" role="group">
                <a asp-action="Edit" asp-route-id="@item.ClearanceId" class="btn btn-primary">Edit</a>
                <a asp-action="Details" asp-route-id="@item.ClearanceId" class="btn btn-info">Details</a>
                <a asp-action="Delete" asp-route-id="@item.ClearanceId" class="btn btn-danger">Delete</a>
            </div>
        </td>
    </tr>
}
```
