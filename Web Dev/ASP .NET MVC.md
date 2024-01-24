[[Bootcamp Notes]]
---

# What is ASP .NET
Simplified interaction between HTML and SQL databases facilitated by C#.
# Getting Started
1. Initialize a ASP .NET MVC project in Visual Studio
*ensure that you have already created a database that you're going to use*

2. Install NuGet Packages
```
EntityFrameworkCore
EntityFrameworkCore.Tools
EntityFrameworkCore.Design
EntityFrameworkCore.SqlServer
```

3. In the NuGet Package Manager Console
```
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

## The Second Circle of Hell
After being successful in calling 