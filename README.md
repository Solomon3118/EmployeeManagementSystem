# Employee Management System

A web-based Employee Management System built with **ASP.NET Core MVC**, **Entity Framework Core**, and **SQLite**.

This project demonstrates practical implementation of CRUD operations, database integration, form validation, search and sorting, dependency injection, service-layer architecture, and a dashboard for employee statistics.

## 🚀 Features

* Create new employees
* View all employees
* View individual employee details
* Edit employee information
* Delete employees with confirmation
* Search employees by name or department
* Sort employees by name or salary
* Form validation
* Total employee count
* Average salary calculation
* SQLite database persistence
* Entity Framework Core migrations
* Dependency Injection
* Service Layer architecture
* Responsive Bootstrap-based interface

## 🛠️ Technologies Used

* **C#**
* **ASP.NET Core MVC**
* **.NET 10**
* **Entity Framework Core**
* **SQLite**
* **Razor Views**
* **Bootstrap**
* **LINQ**
* **Dependency Injection**

## 🏗️ Architecture

The application follows the MVC pattern with a separate Service Layer:

```text
Browser
   │
   ▼
EmployeeController
   │
   ▼
EmployeeService
   │
   ▼
EmployeeDbContext
   │
   ▼
SQLite Database
```

### Controller

`EmployeeController` handles HTTP requests, model validation, routing, and selecting the appropriate views.

### Service Layer

`EmployeeService` contains employee-related operations such as:

* Retrieving employees
* Searching employees
* Sorting employees
* Creating employees
* Updating employees
* Deleting employees
* Retrieving individual employees
* Calculating employee statistics

### Models

The Models layer contains the employee entity, database context, and view model used by the application.

### Views

Razor `.cshtml` files provide the user interface for:

* Employee list
* Create employee
* Edit employee
* Delete confirmation
* Employee details

### Database

SQLite is used as the application's relational database, with Entity Framework Core handling database access and migrations.

## 📂 Project Structure

```text
EmployeeManagementSystem/
│
├── Controllers/
│   └── EmployeeController.cs
│
├── Models/
│   ├── Employee.cs
│   ├── EmployeeDbContext.cs
│   └── EmployeeIndexViewModel.cs
│
├── Services/
│   └── EmployeeService.cs
│
├── Views/
│   └── Employee/
│       ├── Index.cshtml
│       ├── Create.cshtml
│       ├── Edit.cshtml
│       ├── Delete.cshtml
│       └── Details.cshtml
│
├── Migrations/
│
├── wwwroot/
│
├── Program.cs
├── EmployeeManagementSystem.csproj
├── employees.db
└── README.md
```

## 🔄 CRUD Operations

The application implements the complete CRUD lifecycle:

| Operation | Description                        |
| --------- | ---------------------------------- |
| Create    | Add a new employee                 |
| Read      | Display employee records           |
| Update    | Edit existing employee information |
| Delete    | Remove an employee                 |
| Details   | View an individual employee        |

## 🔎 Search & Sorting

Employees can be searched by:

* Name
* Department

Employees can also be sorted by:

* Name
* Salary

Search and sorting are implemented using LINQ with Entity Framework Core.

## ✅ Validation

Employee information is validated using ASP.NET Core Data Annotations.

Example:

```csharp
[Required(ErrorMessage = "Name is required")]
public string Name { get; set; } = string.Empty;

[Required(ErrorMessage = "Department is required")]
public string Department { get; set; } = string.Empty;

[Range(0, 100000000, ErrorMessage = "Salary must be greater than or equal to 0")]
public decimal Salary { get; set; }
```

Invalid form submissions are rejected and appropriate validation messages are displayed to the user.

## 📊 Dashboard

The application includes a dashboard summary displaying:

* **Total Employees**
* **Average Salary**

These statistics are calculated by the `EmployeeService` and passed to the Razor View through `EmployeeIndexViewModel`.

## 💉 Dependency Injection

ASP.NET Core's built-in Dependency Injection container is used throughout the application.

The `EmployeeService` is registered in `Program.cs`:

```csharp
builder.Services.AddScoped<EmployeeService>();
```

The service is then injected into the controller:

```csharp
public EmployeeController(EmployeeService service)
{
    _service = service;
}
```

The `EmployeeService` receives `EmployeeDbContext` through constructor injection:

```csharp
public EmployeeService(EmployeeDbContext context)
{
    _context = context;
}
```

This keeps the controller separated from direct database operations.

## 🗄️ Database

The application uses **SQLite** with Entity Framework Core.

The database connection is configured in `Program.cs`:

```csharp
builder.Services.AddDbContext<EmployeeDbContext>(options =>
    options.UseSqlite("Data Source=employees.db"));
```

Entity Framework Core migrations are used to create and update the database schema.

## ⚙️ Getting Started

### Prerequisites

Make sure you have:

* [.NET 10 SDK](https://dotnet.microsoft.com/)
* Visual Studio, Visual Studio Code, or another C# development environment
* Git

### Clone the Repository

```bash
git clone https://github.com/Solomon3118/EmployeeManagementSystem.git
```

Navigate to the project:

```bash
cd EmployeeManagementSystem
```

### Restore Dependencies

```bash
dotnet restore
```

### Apply Database Migrations

```bash
dotnet ef database update
```

### Run the Application

```bash
dotnet run
```

The terminal will display the local URL where the application is running.

Open that URL in your browser and navigate to the Employee Management System.

## 🧪 Testing the Application

The main functionality can be tested through the following workflow:

1. Add a new employee.
2. Verify the employee appears in the employee list.
3. Search for the employee by name or department.
4. Sort employees by name or salary.
5. Open the employee's Details page.
6. Edit the employee information.
7. Delete the employee.
8. Restart the application and verify that the data remains stored in SQLite.
9. Test validation using empty fields and invalid salary values.

## 🎯 Learning Objectives

This project was developed to gain practical experience with:

* ASP.NET Core MVC
* C#
* Razor Views
* Entity Framework Core
* SQLite
* CRUD operations
* Model binding
* Data validation
* LINQ
* Dependency Injection
* Service Layer architecture
* MVC separation of concerns
* Database migrations
* Working with relational databases

## 🔮 Future Improvements

Possible future enhancements include:

* User authentication and authorization
* Role-based access control
* Employee profile images
* Department management
* Pagination
* Advanced filtering
* Ascending and descending sorting
* Unit testing
* Integration testing
* Logging
* REST API endpoints
* Improved dashboard analytics

## 👨‍💻 Author

**Solomon**

GitHub:
https://github.com/Solomon3118

---

⭐ If you find this project useful, feel free to explore the code and provide feedback.
