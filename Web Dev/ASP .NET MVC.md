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