﻿## Entity Framework Core PostgreSQL Integration

> See [Entity Framework Core Integration document](../Entity-Framework-Core.md) for the basics of the EF Core integration.

### EntityFrameworkCore Project Update

- In `Acme.BookStore.EntityFrameworkCore` project replace package `Volo.Abp.EntityFrameworkCore.SqlServer` with `Volo.Abp.EntityFrameworkCore.PostgreSql` 
- Update to use PostgreSQL in `BookStoreEntityFrameworkCoreModule`. 

1. **Do** Replace the `AbpEntityFrameworkCoreSqlServerModule` with the `AbpEntityFrameworkCorePostgreSqlModule`
2. **Do** Replace the `options.UseSqlServer()` with the `options.UsePostgreSql()`

### Update Connection String Settings
- **Do** Update the PostgreSQL connection string in all `appsettings.json` files.

### Regenerate Initial igration & Update the Database
Open the **Package Manager Console (PMC)** (under the *Tools/Nuget Package Manager* menu), select the `Acme.BookStore.EntityFrameworkCore.DbMigrations` as the **default project** and execute the following command:
> Ensure your startup project is correcty set.

#### Delete Existing Initial Migrations

![postgresql-delete-initial-migrations](images/postgresql-delete-initial-migrations.png)

Then create a new migration class inside the `Migrations` folder.

````
PM> Add-Migration Initial
````

Then execute the `Update-Database` command to update the database schema:

````
PM> Update-Database
````

![postgresql-update-database](images/postgresql-update-database.png)
