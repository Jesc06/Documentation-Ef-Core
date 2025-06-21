# EntityFrameworkCore Set up guide Asp.NetCore MVC

--- 
 
## ✅ Prerequisites

- ✅ Visual Studio 2022 installed
- ✅ .NET 8.0 or .NET 9.0 SDK installed

---

## 🛠️ Setup Instructions


### 1. Create Model Class
```csharp
using System.ComponentModel.DataAnnotations;

namespace Asp.NetCore_MVC_Practice.Models
{
    public class DbTable
    {
        [Key]
        public int Id { get; set; }
        [Required]
        public string Name { get; set; }
        public int age { get; set; } 
    }
}

```


### 2. Create a new folder in your project, add a C# class file, then add the following code.
```csharp
using Asp.NetCore_MVC_Practice.Models;
using Microsoft.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore.Diagnostics;

namespace Asp.NetCore_MVC_Practice.EntityDbData
{
    public class ApplicationDbContext : DbContext
    {
        public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options) : base (options)
        {

        }
        public DbSet<DbTable> StudentInfo { get; set; }
    }
}


```


### 3. Add the following configuration to the Program.cs file.
```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddDbContext<ApplicationDbContext>(options=> options.UseSqlServer(builder.Configuration.GetConnectionString("DbConnection")));
	
var app = builder.Build();
```

### 3. add-Migration ang update-database using Package Manager Console in Visual Studio 2022
```csharp
add-Migration
update-database
```


---
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

Made with ❤️ by John Joshua Manalo Escarez






