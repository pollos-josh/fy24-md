[[Bootcamp Notes]]
---
# ADO .NET
Allows devs to interact with databases, read and write data, and perform typical database actions.

## Data Providers
Specific libraries provided by Microsoft to facilitate data access and interaction with database systems.
## Data Set


```csharp
string connectionString = "Data Source=.Initial"
```

# Best Practices
- Don't hardcode connection string in source code. It should be in `appsettings.json` with other configuration settings/files.