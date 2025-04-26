
# 💼 Loan Management System  
### .NET Core MVC + Neon PostgreSQL Setup Guide

This guide helps you build a full-stack **Loan Management System** using **ASP.NET Core MVC** and **Neon PostgreSQL**, with full **CRUD support** for loan data.

---

## ✅ Step 1: Create a GitHub Repository

Create a new repository named:

```bash
loan-management-system
```

You can do this directly on GitHub or using Git CLI.

---

## ✅ Step 2: Create a New ASP.NET Core MVC Project

```bash
dotnet new mvc -n LoanManagementSystem
cd LoanManagementSystem
```

---

## ✅ Step 3: Install Required NuGet Packages

```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
```

---

## ✅ Step 4: Install Entity Framework Core Tools

```bash
dotnet tool install --global dotnet-ef
exec $SHELL  # reload your shell if needed
```

---

## ✅ Step 5: Scaffold DbContext and Models from Neon PostgreSQL

> Replace connection string with your actual Neon credentials.

```bash
dotnet ef dbcontext scaffold "Host=your-neon-host;Database=your-db-name;Username=your-username;Password=your-password;SSL Mode=Require;Trust Server Certificate=true" Npgsql.EntityFrameworkCore.PostgreSQL -o Models
```

---

## ✅ Step 6: Add Code Generator and Scaffold Controllers with Views

### Install Code Generator

```bash
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet add package Microsoft.EntityFrameworkCore.Tools
dotnet tool install -g dotnet-aspnet-codegenerator
```

### Scaffold Controllers and Views

```bash
dotnet aspnet-codegenerator controller -name CustomersController -m Customer -dc LoanManagementDbContext --relativeFolderPath Controllers --useDefaultLayout --referenceScriptLibraries
dotnet aspnet-codegenerator controller -name LoansController -m Loan -dc LoanManagementDbContext --relativeFolderPath Controllers --useDefaultLayout --referenceScriptLibraries
dotnet aspnet-codegenerator controller -name PaymentsController -m Payment -dc LoanManagementDbContext --relativeFolderPath Controllers --useDefaultLayout --referenceScriptLibraries
```

*(Repeat for other tables like Employees, Collateral, Guarantors, etc.)*

---

## ✅ You're Done!

You now have a fully working ASP.NET Core MVC application connected to your **Neon PostgreSQL** database with CRUD operations ready to go.

