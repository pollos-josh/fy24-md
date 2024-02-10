[[ADO .NET]]
---

# Basic ADO.NET Syntax

## Establishing a Connection

```csharp
using System.Data.SqlClientl
using Microsoft.Extensions.Configuration

IConfiguration configuration = new ConfigurationBuilder()
		.AddJsonFile("appsettings.json", false, true)
		.Build();

string? connectionString = configuration.getConnectionString("LocalSqlConnection");

using (SqlConnection connection = new SqlConnection("LocalSqlConnection")) {
	//sql
}
```

*this whole code block just establishes a connection with the database in `appsettings.json`*

In Azure, find connection string settings, get the `ADO connection string` add it in `appsettings.json`.

use `AzureSqlConnection` as a variable to hold the string.

## While (reader.Read());

A construct loop to iterate through rows returned by SQL. `ExecuteReader()` returns an object called `SqlDataReader` and `while(reader.Read())` allows you to sequentially read the rows returned.

As long as there are rows, `while(reader.Read())` will iterate through the rows.

Basically, access all rows returned.

```csharp
while (reader.Read()){ 
	var columnName = reader["columnName"]; // in c# get the column name per row
	var columnName2 = reader["columnName2"]; // and push them into variables 

	Console.WriteLine[$"column1 = {columnName}, column2 = {columnName2}"];
}
```

## Working with Params

We're going to pass variables then bind them to the query.

```csharp
string connectionString = "connection string";

string userName = "username";
string customerName = "customerName";

string query = "SELECT * FROM dbo.Customer"
				"WHERE username = @userName AND customerName = @customerName";

using (SqlConnection connection = new SqlConnection(connectionString)) { // establish connection
	SqlCommand command = new SqlCommand(query, connection); //construct sql command
	command.Parameters.AddWithValue("@userName", userName); //bind userName var with @userName query
	command.Parameters.AddWithValue("@customerName", customerName); //same thing here

	
}
```

## Executing Queries

For commands that don't return data e.g. `INSERT`, `UPDATE`, `DELETE`

```csharp
string query = 'INSERT INTO table_name (Col1, Col2) VALUES (val1, val2)';
SqlCommand command = new SqlCommand(query, connection);

command.Parameters.AddWithValue("@Value1", value1);
command.Parameters.AddWithValue("@Value2", value2);

connection.Open();
int rowsAffected = command.ExecuteNonQuery();
connection.Close();
```

For commands that return data `SELECT`

```csharp
string query = "SELECT Col1, Col2 FROM TableName";
SqlCommand command = new SqlCommand(query, connection);

connection.Open();
SqlDataReader = new SqlCommand(query, connection);

while (reader.Read()) {
	var value1 = reader["Column1"];
	var value2 = reader["Column2"];
}

reader.Close();
connection.Close();
```

------

```csharp
IConfiguration configuration = new ConfigurationBuilder()
		.AddJsonFile("appsettings.json", false, true)
		.Build();

string? connectionString = configuration.getConnectionString("LocalSqlConnection");

using (SqlConnection connection = new SqlConnection("LocalSqlConnection")) {
	
	int customerID = 1;
	string selectString = "SELECT * FROM dbo.Customer WHERE CustomerID = @CustomerID";

	SqlCommand selectCommand = new SqlCommand(selectString, connection);

	SqlParameter customerIDParameter = new SqlParameter();
	customerIDParameter.ParameterName = "@CustomerID";
	customerIDParameter.Value = customerID;

	selectCommand.Parameters.Add(customerIDParameter);

	connection.Open();

	SqlDataReader reader = selectCommand.ExecuteReader();

	if (reader.HasRows)
	{
		while (reader.Read())
		{
			Console.WriteLine("Customer Name: {0} {1} {2}",
				reader["FirstName"],
				reader["MiddleName"],
				reader["LastName"]);
		}
	}

	reader.Close();
}
```

This one is a sample snippet to establish a connection with a database. It also declares an `int customerID = 1` then passes it as a param with

```csharp
SqlParameter customerIDParameter = new SqlParameter();
customerIDParameter.ParameterName = "@CustomerID";
customerIDParameter.Value = customerID;
//long form statement to push customerID into SelectCommand

SqlParameter customIDParameter = new SqlParameter("@CustomerID", customerID);
//constructor to directly call the int parameter

selectCommand.Parameters.Add(new SqlParameter("@CustomerID, customerID")); 
//directly push the customerID into SelectCommand
```
