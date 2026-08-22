# 🏠 HostelMate – Hostel Management System

HostelMate is a web-based hostel management system designed to simplify and automate hostel-related activities for students, managers, and administrators.

The system provides role-based access for **Students, Managers, and Admins**, allowing users to manage leave applications, announcements, mess information, user accounts, and administrative workflows through dedicated dashboards.

---

## 🚀 Features

### 👨‍🎓 Student

- Student registration and authentication
- Student profile management
- Apply for hostel leave
- View leave status
- View leave calendar
- View hostel announcements
- View mess menu
- Manage account information

### 👨‍💼 Manager

- Manager authentication
- Manager dashboard
- View pending leave requests
- Approve or reject leave applications
- View approved leaves
- View rejected leaves
- View closed leaves
- Manage hostel announcements
- Manage mess menu

### 👨‍💻 Admin

- Secure admin authentication
- Admin dashboard
- User directory
- Manage hostel managers
- Monitor leave applications
- View system overview
- Role-based access control

---

## 🛠️ Technologies Used

### Frontend

| Technology | Purpose |
|------------|---------|
| React.js | Building reusable UI components |
| JavaScript (ES6+) | Application logic |
| JSX | Writing React components |
| React Router | Client-side routing and navigation |
| CSS | Styling and responsive UI |
| Vite | Frontend development server and build tool |

### Backend

| Technology | Purpose |
|------------|---------|
| Node.js | JavaScript runtime |
| Express.js | Backend server and API layer |
| JavaScript | Backend application logic |
| CORS | Cross-origin request handling |
| dotenv | Environment variable management |

### Database & Authentication

| Technology | Purpose |
|------------|---------|
| Supabase | Backend-as-a-Service |
| PostgreSQL | Relational database |
| Supabase Auth | User authentication |
| Row-level application roles | Student/Manager/Admin access control |

### Development Tools

- Git
- GitHub
- Visual Studio Code
- npm
- Vite

---

## 🏗️ System Architecture

HostelMate follows a client-server architecture.

```text
                    ┌──────────────────────┐
                    │       User           │
                    │ Student / Manager    │
                    │       / Admin        │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │      React.js        │
                    │      Frontend        │
                    └──────────┬───────────┘
                               │
                     HTTP / API Requests
                               │
                               ▼
                    ┌──────────────────────┐
                    │     Express.js       │
                    │       Backend        │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │       Supabase       │
                    │ Authentication + DB  │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │      PostgreSQL      │
                    │      Database        │
                    └──────────────────────┘
