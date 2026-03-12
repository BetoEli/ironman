# 🏋️ Iron Man Fit

A full-stack fitness tracking web application built with **ASP.NET Core 7 Razor Pages**. Users can log workouts, track exercise history, and create custom routines — all secured behind an authentication system.

---

## 📸 UI Screenshots

### Dashboard / Home
![Home Dashboard](https://github.com/user-attachments/assets/0a339622-99c1-49f6-b77f-a64140cbec91)

### Collapsible Sidebar Navigation
![Sidebar Expanded](https://github.com/user-attachments/assets/e3c9ebb3-ca64-40f8-a924-3d0fc363607a)

### Start Workout
![Start Workout](https://github.com/user-attachments/assets/d2e86128-30d6-4d06-b57e-79f5346958d6)

### Past Workouts
![Past Workouts](https://github.com/user-attachments/assets/08a671fe-a82e-4808-af32-961771befc7e)

### Routines
![Routines](https://github.com/user-attachments/assets/488b0ed5-1696-4b27-9546-bcd6377a7c88)

### Login
![Login](https://github.com/user-attachments/assets/87a1c55e-6f8d-422c-a775-0a6b7b216996)

### Register
![Register](https://github.com/user-attachments/assets/9c191e52-b40e-4384-a1a4-665c663a345a)

---

## 📋 Project Scope

Iron Man Fit is a fitness tracking web application designed to help users:

- **Log workouts** — record exercise type, duration, distance, and date
- **Review history** — view all past workouts in a sortable table
- **Build routines** — create named workout routines with custom exercise lists
- **Manage accounts** — register, log in, and manage user profiles securely

The project serves as a practical, end-to-end demonstration of modern .NET web development, covering everything from database design and authentication to server-side rendering and client-side interactivity.

---

## 🏗️ Architecture

Iron Man Fit follows the **Razor Pages** pattern (a variant of MVC built into ASP.NET Core):

```
ironman/
├── Data/
│   ├── ApplicationDbContext.cs      # EF Core DbContext (Identity schema)
│   └── Migrations/                  # Auto-generated database migrations
├── Pages/
│   ├── Index.cshtml                 # Dashboard (Workouts, Routines UI)
│   ├── Index.cshtml.cs              # Dashboard PageModel (server-side logic)
│   ├── Privacy.cshtml               # Privacy policy page
│   ├── Error.cshtml                 # Error handling page
│   └── Shared/
│       ├── _Layout.cshtml           # Master layout (navbar, footer, scripts)
│       ├── _LoginPartial.cshtml     # Login/Logout partial component
│       └── _ValidationScriptsPartial.cshtml
├── wwwroot/
│   ├── css/site.css                 # Custom styles (sidebar, theme, layout)
│   ├── js/site.js                   # Client-side workout/routine logic
│   └── lib/bootstrap/               # Bootstrap 5 framework
├── Properties/
│   └── launchSettings.json          # Dev launch profiles (ports, env)
├── Program.cs                       # App startup, DI container, middleware
├── appsettings.json                 # App configuration (connection strings)
└── ironman.csproj                   # Project file & NuGet dependencies
```

### Layer Responsibilities

| Layer | Files | Responsibility |
|-------|-------|---------------|
| **View** | `*.cshtml` | Razor templates — HTML + C# markup |
| **Page Model** | `*.cshtml.cs` | Request handlers (`OnGet`, `OnPost`) |
| **Data** | `ApplicationDbContext.cs` | EF Core database access |
| **Client Logic** | `wwwroot/js/site.js` | DOM manipulation, form handling |
| **Styling** | `wwwroot/css/site.css` | Custom theme, sidebar, layout |

### Key Design Decisions

- **Razor Pages over MVC Controllers** — keeps each page self-contained (`.cshtml` + `.cshtml.cs`)
- **ASP.NET Identity** — built-in authentication with email confirmation
- **SQLite** — zero-config local database, easily swapped for SQL Server
- **Bootstrap 5** — responsive grid and UI components
- **Client-side state** — workout/routine data currently managed in the DOM (ready to wire to a backend API)

---

## ⚡ Quick Start

### Prerequisites

- [.NET 7 SDK](https://dotnet.microsoft.com/download/dotnet/7.0)
- Visual Studio 2022, VS Code with C# extension, or any terminal

### 1. Clone the Repository

```bash
git clone https://github.com/BetoEli/ironman.git
cd ironman
```

### 2. Restore Dependencies

```bash
dotnet restore
```

### 3. Apply Database Migrations

```bash
dotnet ef database update
```

> If `dotnet ef` is not found, install it with:
> ```bash
> dotnet tool install --global dotnet-ef
> ```

### 4. Run the Application

```bash
dotnet run
```

Then open your browser at:
- **HTTP**: http://localhost:5174
- **HTTPS**: https://localhost:7150

### 5. Register an Account

Navigate to `/Identity/Account/Register` to create a new account, then log in to access the full dashboard.

---

## 🛠️ Tech Stack

| Category | Technology | Purpose |
|----------|-----------|---------|
| **Framework** | ASP.NET Core 7.0 | Web application host & middleware pipeline |
| **Language** | C# 11 | Server-side logic |
| **UI Engine** | Razor Pages | Server-side HTML rendering with C# |
| **ORM** | Entity Framework Core 7 | Database access & migrations |
| **Auth** | ASP.NET Identity | User registration, login, password hashing |
| **Database** | SQLite | Local relational database (dev/prod) |
| **CSS Framework** | Bootstrap 5 | Responsive layout & UI components |
| **Icons** | Font Awesome 6 | Sidebar and navigation icons |
| **Client JS** | Vanilla JavaScript | DOM manipulation, form interactions |
| **IDE** | Visual Studio 2022 / VS Code | Development environment |

---

## 📚 What You'll Learn Building This Project

### 1. ASP.NET Core Fundamentals
- Setting up the middleware pipeline in `Program.cs`
- Dependency injection for services (DbContext, Identity, Logging)
- Configuration management with `appsettings.json` and User Secrets
- Static file serving and routing

### 2. Razor Pages Pattern
- Creating `PageModel` classes with `OnGet` / `OnPost` handlers
- Using Tag Helpers (`asp-for`, `asp-action`, `asp-controller`)
- Shared layouts, partial views, and `_ViewImports`
- Model binding and form validation

### 3. Entity Framework Core & Databases
- Configuring a `DbContext` and connecting to SQLite
- Writing and applying migrations (`dotnet ef migrations add`, `dotnet ef database update`)
- Understanding the Identity schema (Users, Roles, Claims tables)
- Extending `IdentityDbContext` with custom domain entities

### 4. Authentication & Security
- Integrating ASP.NET Identity for registration and login
- Email confirmation workflows and account management
- Password hashing and secure session management
- Protecting routes with `[Authorize]`

### 5. Frontend Development with Razor + Bootstrap
- Structuring responsive layouts with Bootstrap's grid system
- Building a collapsible CSS sidebar with hover transitions
- Styling with custom CSS properties and flexbox
- Integrating Font Awesome icons

### 6. Client-Side JavaScript
- Handling HTML form submissions with JavaScript
- Dynamically adding rows to a DOM table
- Tab-style section toggling (show/hide content panels)
- Preparing for `fetch()` API calls to a backend

### 7. Full-Stack Integration
- Connecting server-rendered pages to a live database
- Passing data between `PageModel` and `.cshtml` view
- Handling errors with custom error pages and `ILogger`
- Configuring launch profiles and environment-specific settings

### 8. Project Structure Best Practices
- Organizing a .NET web project (`Pages`, `Data`, `wwwroot`, `Properties`)
- Using `.gitignore` for build artifacts and secrets
- Understanding the `.csproj` file and NuGet package references
- Running migrations at startup vs. manually via CLI

---

## 🗺️ Roadmap

- [ ] Persist workout data to the database via `OnPost` handlers
- [ ] Add REST API endpoints (`/api/workouts`, `/api/routines`)
- [ ] Replace in-memory JS state with `fetch()` API calls
- [ ] Add workout history charts with Chart.js
- [ ] Implement pagination and filtering for Past Workouts
- [ ] Add user profile page with fitness goals
- [ ] Write xUnit integration tests
- [ ] Deploy to Azure App Service

---

## 📄 License

This project is open source. Feel free to use it as a learning reference or starting point for your own fitness app.
