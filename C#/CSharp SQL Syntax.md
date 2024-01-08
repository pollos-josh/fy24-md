[[ADO .NET]]
---

```csharp
command object.ExecuteReader() //data retrieval
command object.ExecuteNonQuery() //data manipulation
command object.ExecuteScalar() //query with aggregate functions
```
Basic ADO.NET Syntax

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