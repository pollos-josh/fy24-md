[[Bootcamp Notes]]
---

# What is ASP .NET

Simplified interaction between HTML and SQL databases facilitated by C#.

# Getting Started
1. Initialize a ASP .NET MVC project in Visual Studio
*ensure that you have already created a database that you're going to use*

2. Install NuGet Packages

```csharp
EntityFrameworkCore
EntityFrameworkCore.Tools
EntityFrameworkCore.Design
EntityFrameworkCore.SqlServer
```

3. In the NuGet Package Manager Console

```csharp
Scaffold-DbContext "Data Source=*server name*;Initial Catalog=*databse name*;Integrated Security=True;Encrypt=False" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models -Context *dbContextName*
```

*this will create models and classes from your database*

4. Run `Add-Migration InitialMigration` and `Update-Database`

5. Fix the `ConnectionString` in `appsettings.Development.json`

6. Add this before `var app = builder.Build();`

```csharp
builder.Services.AddDbContext<*dbContextName*>(options => 
	options.UseSqlServer(builder.Configuration.GetConnectionString("databaseName")));
```

---

# The @item.IslandImage.IslandImageURL Fiasco

It started all because I didn't fix my database in advance.

**You have to ensure that your database is already fixed beforehand. VERY IMPORTANT**

Change is the enemy of polymorphism, and this is the most polymorphed out of all polymorphisms.

## Back on the Appalachian Trail (Getting Started)

Starting from scratch, I made a fresh new solution with `ASP .NET Model-View-Controller`.

Install all dependencies

- *EntityFrameworkCore*
- *EntityFrameworkCore.Design*
- *EntityFrameworkCore.Tools*
- *EntityFrameworkCore.SqlServer*

Make sure the connection string is in

```json
//appsettings.json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "Allowed-Hosts": "*" <-- delete this
  "ConnectionString": "*" <-- replace with this
}
```

In Nuget Package Manager console, do the `Scaffold-DbContext` command. Run `Add-Migration`.

In `Program.cs` add

```csharp
using Microsoft.EntityFrameworkCore;
using WebApplication3.Models; //intelli sense should detect what namespace the DbContext Models are in
```

Also add this before `var app = build()`

```csharp
        builder.Services.AddDbContext<*dbContextName*>(options => 
            options.UseSqlServer(builder.Configuration.GetConnectionString("databaseName")));
```

Then add an `MVC Controller Entity Framerwork with Views` on the Folder Views. 

*Make sure that you select the main table that you want to work with. It has to have all the necessary relations with other tables or it'll be fucked.*

This generates all the code you need and hopefully, all the spaghetti has been straightened out.

### DON'T EVEN TRY TO MODIFY THE FRAMEWORK YOURSELF. DON'T ADD CONSTRUCTORS OR ANYTHING MANUALLY BECAUSE YOU WILL FUCK UP.
### USE THE SCAFFOLD. USE THE FRAMEWORK COMMANDS. THANKS.

# Many-to-Many Relationships

## Tags and What Went Wrong (again)

The spirit of the Appalachian Trail, I overhauled the database again, adding `dbo.Tags` table so that *Islands* is at least at **2nd Normalization**. And I also added a table junction to establish a `Many-to-Many` relationship from `dbo.Islands` -> `dbo.Tags`. I did all the correct steps and made sure the relationships were all good. Skipping to what went wrong:

- After scaffolding, make sure to double check the `Models` if each and every relation is functioning properly. We can use father *ChatGPT* for that.
- Renew the MVC Controller with Entity Framework. It doesn't fix everything but it helps.

After all of the comes the most important part.

## IslandController.cs

Be very sure that the external table, in my case `Tags` is accessible through the parent table, which is `Islands`. In the view methods in `IslandController.cs`, I added

```csharp
public async Task<IActionResult> Index()
{
	var appDbContext = _context.Islands
		.Include(i => i.IslandImage)
		.Include(i => i.Tags); // <--- ADD THIS
	return View(await appDbContext.ToListAsync());
}
```

`.Include(i => i.Tags` establishes the connection in `Index()`. The connection is there at the backend but the method doesn't really realize the connection until it is included. I also added that in `Details()`.

```csharp
public async Task<IActionResult> Details(int? id)
{
	if (id == null)
	{
		return NotFound();
	}
	var island = await _context.Islands
		.Include(i => i.IslandImage)
		.Include(i => i.Tags) // Include the Tags for the island
		.FirstOrDefaultAsync(m => m.IslandId == id);

	if (island == null)
	{
		return NotFound();
	}
	return View(island);
}
```

It's better to have *ChatGPT* establish the connection unless you know the syntax (which I don't at the moment).

--- 
# Partial View

Make an empty `Razor` view. It should have the extension `.cshtml`. Plop in a section of the website

```html
 <nav class="navbar navbar-expand-sm navbar-toggleable-sm navbar-light bg-white border-bottom box-shadow mb-3">
    <div class="container-fluid">
        <a class="navbar-brand" asp-area="" asp-controller="Home" asp-action="Index">WebApplication3</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target=".navbar-collapse" aria-controls="navbarSupportedContent"
                aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="navbar-collapse collapse d-sm-inline-flex justify-content-between">
            <ul class="navbar-nav flex-grow-1">
                <li class="nav-item">
                    <a class="nav-link text-dark" asp-area="" asp-controller="Home" asp-action="Index">Home</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link text-dark" asp-area="" asp-controller="Home" asp-action="Privacy">Privacy</a>
                </li>
            </ul>
        </div>
    </div>
</nav>
```

This is a bootstrapped Navbar. Name it `_Something`.

Then call it in a page with

```csharp
<partial name = "_Something" />
```

This will general the partial class.
