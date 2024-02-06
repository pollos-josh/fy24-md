```html
<div class="container">
    <form asp-action="Edit" enctype="multipart/form-data">
        <div class="row">
            <div class="col-md-4">
                <div asp-validation-summary="ModelOnly" class="text-danger"></div>
                <input type="hidden" asp-for="ClearanceId" />

                <div class="form-group required py-2">
                    <label asp-for="BranchId" class="control-label">Branch ID</label>
                    <select asp-for="BranchId" class="form-control" asp-items="ViewBag.BranchName" required></select>
                    <span asp-validation-for="BranchId" class="text-danger"></span>
                </div>

                <div class="form-group required pt-2 pb-2">
                    <label asp-for="ValidId" class="control-label">Valid ID</label>
                    <select asp-for="ValidId" class="form-control" asp-items="ViewBag.ValidIdname" required></select>
                    <span asp-validation-for="ValidId" class="text-danger"></span>
                </div>

                <div class="form-group py-2">
                    <label asp-for="ValidIdUrl" class="control-label">Upload Valid ID</label>
                    <input asp-for="ValidIdUrl" name="ValidIdImage" class="form-control" type="file"  accept=".png, .jpg, .jpeg" />
                    <span asp-validation-for="ValidIdUrl" class="text-danger"></span>
                </div>

				<div class="form-group py-2">
				    <label asp-for="ImageUrl" class="control-label">Applicant Photo</label>
				    <input asp-for="ImageUrl" name="Profile" class="form-control" type="file" accept=".png, .jpg, .jpeg" />
				</div>
            </div>

            <div class="col-md-4">

            </div>

            <div class="col-md-4">
                <!-- Your form fields here -->
            </div>

            <!-- Add more columns if needed -->

            <!-- Submit Button -->
            <div class="col-md-12 form-group py-2">
                <input type="Submit" value="Save" class="btn btn-primary" />
            </div>
        </div>
    </form>
</div>

```