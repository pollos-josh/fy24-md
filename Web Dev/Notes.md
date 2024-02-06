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
                <div class="form-group py-2 required">
                    <label asp-for="LastName" class="control-label">Last Name</label>
                    <input asp-for="LastName" class="form-control" required />
                    <span asp-validation-for="LastName" class="text-danger"></span>
                </div>

                <div class="form-group py-2 required">
                    <label asp-for="FirstName" class="control-label">First Name</label>
                    <input asp-for="FirstName" class="form-control" required />
                    <span asp-validation-for="FirstName" class="text-danger"></span>
                </div>

                <div class="form-group pt-2">
                    <label asp-for="MiddleName" class="control-label">Middle Name</label>
                    <input asp-for="MiddleName" class="form-control" id="middleNameInput" />
                    <span asp-validation-for="MiddleName" class="text-danger"></span>
                </div>

                <div class="form-group pb-2">
                    <label>
                        <input type="checkbox" id="disableMiddleNameCheckbox" onchange="toggleMiddleNameField()" />
                        No Middle Name
                    </label>
                </div>

                <div class="form-group py-2 required">
                    <label asp-for="DateOfBirth" class="control-label">Date of Birth</label>
                    <input type="date" asp-for="DateOfBirth" class="form-control" required />
                    <span asp-validation-for="DateOfBirth" class="text-danger"></span>
                </div>
            </div>

            <div class="col-md-4">
                <div class="form-group py-2">
                    <label asp-for="Religion" class="control-label"></label>
                    <input asp-for="Religion" class="form-control" />
                    <span asp-validation-for="Religion" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="Religion" class="control-label"></label>
                    <input asp-for="Religion" class="form-control" />
                    <span asp-validation-for="Religion" class="text-danger"></span>
                </div>
                <div class="form-group py-2 required">
                    <label asp-for="Height" class="control-label"></label>
                    <input asp-for="Height" class="form-control" required />
                    <span asp-validation-for="Height" class="text-danger"></span>
                </div>
                <div class="form-group py-2 required">
                    <label asp-for="Weight" class="control-label"></label>
                    <input asp-for="Weight" class="form-control" required />
                    <span asp-validation-for="Weight" class="text-danger"></span>
                </div>
                <div class="form-group py-2 required">
                    <label asp-for="GenderId" class="control-label">Sex</label>
                    <select asp-for="GenderId" class="form-control" asp-items="ViewBag.GenderName" required></select>
                    <span asp-validation-for="GenderId" class="text-danger"></span>
                </div>
			 </div>

            <div class="col-md-4">
                <div class="form-group py-2">
                    <label asp-for="EducationId" class="control-label">Education</label>
                    <select asp-for="EducationId" class="form-control" asp-items="ViewBag.EducationName"></select>
                    <span asp-validation-for="EducationId" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="LandlineNumber" class="control-label">Landline Number</label>
                    <input asp-for="LandlineNumber" class="form-control" />
                    <span asp-validation-for="LandlineNumber" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="MobileNumber" class="control-label">Mobile Number</label>
                    <input asp-for="MobileNumber" class="form-control" />
                    <span asp-validation-for="MobileNumber" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="EmailAddress" class="control-label">Email</label>
                    <input asp-for="EmailAddress" class="form-control" />
                    <span asp-validation-for="EmailAddress" class="text-danger"></span>
                </div>
                <div class="form-group py-2 required">
                    <label asp-for="ComplexionId" class="control-label">Complexion</label>
                    <select asp-for="ComplexionId" class="form-control" asp-items="ViewBag.ComplexionType" required></select>
                    <span asp-validation-for="ComplexionId" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="ScarsMarksPeculiarities" class="control-label">Identifying Marks</label>
                    <input asp-for="ScarsMarksPeculiarities" class="form-control" />
                    <span asp-validation-for="ScarsMarksPeculiarities" class="text-danger"></span>
                </div> 
            </div>
            <div class="col-md-4">
                <div class="form-group py-2 required">
                    <label asp-for="CivilStatusId" class="control-label">Civil Status</label>
                    <select asp-for="CivilStatusId" class="form-control" asp-items="ViewBag.CivilStatusName" required></select>
                    <span asp-validation-for="CivilStatusId" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="HusbandOrWifeName" class="control-label">Spouse</label>
                    <input asp-for="HusbandOrWifeName" class="form-control" />
                    <span asp-validation-for="HusbandOrWifeName" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="FatherName" class="control-label">Father's Name</label>
                    <input asp-for="FatherName" class="form-control" />
                    <span asp-validation-for="FatherName" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="FatherPlaceOfBirth" class="control-label">Father Place of Birth</label>
                    <input asp-for="FatherPlaceOfBirth" class="form-control" />
                    <span asp-validation-for="FatherPlaceOfBirth" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="MotherName" class="control-label">Mother's Maiden Name</label>
                    <input asp-for="MotherName" class="form-control" />
                    <span asp-validation-for="MotherName" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="MotherPlaceOfBirth" class="control-label">Mother Place of Birth</label>
                    <input asp-for="MotherPlaceOfBirth" class="form-control" />
                    <span asp-validation-for="MotherPlaceOfBirth" class="text-danger"></span>
                </div>
            </div>
            <div class="col-md-12 form-group py-2">
                <input type="Submit" value="Save" class="btn btn-primary" />
            </div>
        </div>
    </form>
</div>

```




```html
<div class="container">
    <form asp-action="Create" enctype="multipart/form-data">
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
                    <input asp-for="ValidIdUrl" name="ValidIdImage" class="form-control" type="file" accept=".png, .jpg, .jpeg" />
                    <span asp-validation-for="ValidIdUrl" class="text-danger"></span>
                </div>

                <div class="form-group py-2">
                    <label asp-for="ImageUrl" class="control-label">Applicant Photo</label>
                    <input asp-for="ImageUrl" name="Profile" class="form-control" type="file" accept=".png, .jpg, .jpeg" />
                </div>
            </div>

            <div class="col-md-4">
                <div class="form-group py-2 required">
                    <label asp-for="LastName" class="control-label">Last Name</label>
                    <input asp-for="LastName" class="form-control" required />
                    <span asp-validation-for="LastName" class="text-danger"></span>
                </div>

                <div class="form-group py-2 required">
                    <label asp-for="FirstName" class="control-label">First Name</label>
                    <input asp-for="FirstName" class="form-control" required />
                    <span asp-validation-for="FirstName" class="text-danger"></span>
                </div>

                <div class="form-group pt-2">
                    <label asp-for="MiddleName" class="control-label">Middle Name</label>
                    <input asp-for="MiddleName" class="form-control" id="middleNameInput" />
                    <span asp-validation-for="MiddleName" class="text-danger"></span>
                </div>

                <div class="form-group pb-2">
                    <label>
                        <input type="checkbox" id="disableMiddleNameCheckbox" onchange="toggleMiddleNameField()" />
                        No Middle Name
                    </label>
                </div>

                <div class="form-group py-2 required">
                    <label asp-for="DateOfBirth" class="control-label">Date of Birth</label>
                    <input type="date" asp-for="DateOfBirth" class="form-control" required />
                    <span asp-validation-for="DateOfBirth" class="text-danger"></span>
                </div>
            </div>

            <div class="col-md-4">
                <div class="form-group py-2">
                    <label asp-for="Religion" class="control-label"></label>
                    <input asp-for="Religion" class="form-control" />
                    <span asp-validation-for="Religion" class="text-danger"></span>
                <div class="form-group py-2">
                    <label asp-for="Religion" class="control-label"></label>
                    <input asp-for="Religion" class="form-control" />
                    <span asp-validation-for="Religion" class="text-danger"></span>
                </div>
                <div class="form-group py-2 required">
                    <label asp-for="Height" class="control-label"></label>
                    <input asp-for="Height" class="form-control" required />
                    <span asp-validation-for="Height" class="text-danger"></span>
                </div>
                <div class="form-group py-2 required">
                    <label asp-for="Weight" class="control-label"></label>
                    <input asp-for="Weight" class="form-control" required />
                    <span asp-validation-for="Weight" class="text-danger"></span>
                </div>
                <div class="form-group py-2 required">
                    <label asp-for="GenderId" class="control-label">Sex</label>
                    <select asp-for="GenderId" class="form-control" asp-items="ViewBag.GenderName" required></select>
                    <span asp-validation-for="GenderId" class="text-danger"></span>
                </div>
			 </div>

            <div class="col-md-4">
                <div class="form-group py-2">
                    <label asp-for="EducationId" class="control-label">Education</label>
                    <select asp-for="EducationId" class="form-control" asp-items="ViewBag.EducationName"></select>
                    <span asp-validation-for="EducationId" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="LandlineNumber" class="control-label">Landline Number</label>
                    <input asp-for="LandlineNumber" class="form-control" />
                    <span asp-validation-for="LandlineNumber" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="MobileNumber" class="control-label">Mobile Number</label>
                    <input asp-for="MobileNumber" class="form-control" />
                    <span asp-validation-for="MobileNumber" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="EmailAddress" class="control-label">Email</label>
                    <input asp-for="EmailAddress" class="form-control" />
                    <span asp-validation-for="EmailAddress" class="text-danger"></span>
                </div>
                <div class="form-group py-2 required">
                    <label asp-for="ComplexionId" class="control-label">Complexion</label>
                    <select asp-for="ComplexionId" class="form-control" asp-items="ViewBag.ComplexionType" required></select>
                    <span asp-validation-for="ComplexionId" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="ScarsMarksPeculiarities" class="control-label">Identifying Marks</label>
                    <input asp-for="ScarsMarksPeculiarities" class="form-control" />
                    <span asp-validation-for="ScarsMarksPeculiarities" class="text-danger"></span>
                </div> 
            </div>
            <div class="col-md-4">
                <div class="form-group py-2 required">
                    <label asp-for="CivilStatusId" class="control-label">Civil Status</label>
                    <select asp-for="CivilStatusId" class="form-control" asp-items="ViewBag.CivilStatusName" required></select>
                    <span asp-validation-for="CivilStatusId" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="HusbandOrWifeName" class="control-label">Spouse</label>
                    <input asp-for="HusbandOrWifeName" class="form-control" />
                    <span asp-validation-for="HusbandOrWifeName" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="FatherName" class="control-label">Father's Name</label>
                    <input asp-for="FatherName" class="form-control" />
                    <span asp-validation-for="FatherName" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="FatherPlaceOfBirth" class="control-label">Father Place of Birth</label>
                    <input asp-for="FatherPlaceOfBirth" class="form-control" />
                    <span asp-validation-for="FatherPlaceOfBirth" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="MotherName" class="control-label">Mother's Maiden Name</label>
                    <input asp-for="MotherName" class="form-control" />
                    <span asp-validation-for="MotherName" class="text-danger"></span>
                </div>
                <div class="form-group py-2">
                    <label asp-for="MotherPlaceOfBirth" class="control-label">Mother Place of Birth</label>
                    <input asp-for="MotherPlaceOfBirth" class="form-control" />
                    <span asp-validation-for="MotherPlaceOfBirth" class="text-danger"></span>
                </div>
            </div>


            <div class="col-md-12 form-group py-2">
                <input type="Submit" value="Save" class="btn btn-primary" />
            </div>
        </div>
    </form>
</div>

```