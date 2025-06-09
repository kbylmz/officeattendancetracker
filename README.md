# Office Attendance Tracker

A self-hosted internal web application for tracking which days employees plan to attend the office.  
Authentication is done via **Active Directory**, ensuring secure and centralized access for enterprise users.

---

## 🧩 Project Modules

The system includes:

- 🖥 **Web Application (Angular)** — Employee UI for logging in and selecting office attendance days
- ⚙️ **Backend API (.NET Core)** — Handles authentication, attendance data, and Active Directory integration
- 🗄 **Database (MSSQL)** — Stores attendance data securely

---

## 🛠️ Tech Stack

- **Frontend**: Angular 17
- **Backend**: ASP.NET Core 8 Web API
- **Authentication**: Active Directory (via LDAP)
- **Database**: Microsoft SQL Server
- **ORM**: Entity Framework Core

---

## 🔐 Authentication

- Users log in using their corporate Active Directory credentials
- Backend validates credentials securely via LDAP
- No password storage — credentials are passed through directly to AD for validation

---

## 🎯 Core Features

- 🔐 **Secure AD Login**: Integrated with your organization's LDAP directory
- 📆 **Attendance Selection**: Users can mark the days they plan to work from the office
- 💾 **Persistent Storage**: Submissions are saved to a central SQL Server database
- 📊 **Dashboard (optional)**: Admins can view attendance trends

---

## ✅ MVP Requirements

- [x] AD login via username/password
- [x] Calendar-style or checkbox UI for day selection
- [x] Save and update availability data
- [x] Prevent duplicate submissions
- [x] Secure backend API with proper input validation

---

## 📂 Project Structure

```
office-attendance-tracker/
├── backend/                  # ASP.NET Core Web API
│   ├── Controllers/          # API Controllers (Login, Attendance)
│   ├── Services/             # Business logic and LDAP handling
│   ├── Models/               # Data models (User, Attendance, etc.)
│   ├── Data/                 # EF Core DbContext and migrations
│   └── appsettings.json      # App configuration (LDAP, DB, etc.)

├── frontend/                 # Angular Application
│   ├── src/app/
│   │   ├── login/            # Login component
│   │   ├── calendar/         # Calendar component for day selection
│   │   └── services/         # Angular services (auth, attendance)
│   └── angular.json          # Angular CLI configuration

└── README.md                 # Project documentation
```

---

## ⚡ GitHub Copilot Instructions

- Generate **Angular components** for:
  - `login` (AD credentials input)
  - `calendar` (day selection UI)

- Create **API endpoints** in .NET:
  - `POST /api/login` — Validates user credentials against LDAP
  - `GET/POST/PUT /api/attendance` — CRUD operations for office attendance days

- Implement **LDAP authentication** using:
  - `System.DirectoryServices.Protocols` in .NET

- Use **Entity Framework Core** to:
  - Handle database migrations
  - Save and retrieve attendance data

- Design a **simple Angular calendar UI** for selecting days of the week or dates

- Implement **Angular route guards** to:
  - Restrict access to attendance page after login

- Ensure **security best practices**:
  - Input validation on both frontend and backend
  - Enforce HTTPS-only communication
  - Sanitize user inputs
  - Store no credentials locally or in the database

---

## 🔐 Security Notes

- ❌ No user passwords are stored
- ✅ Authentication only occurs via secure **Active Directory bind**
- 🔒 SQL Server connections must enforce **SSL encryption**
- 🌐 All communication between frontend and backend must use **HTTPS**
