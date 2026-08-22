🏠 HostelMate
Smart Hostel Management System

HostelMate is a role-based web application designed to streamline hostel management by providing a centralized platform for students, managers, and administrators to manage hostel-related activities, leave workflows, user management, announcements, and other day-to-day operations.

The application replaces fragmented/manual processes with a structured digital workflow, improving communication and making hostel administration more efficient.

✨ Key Features
👨‍🎓 Student Portal

Students can:

Access a personalized student dashboard
Apply for hostel leave
Track leave status
View leave-related information through the leave calendar
View hostel announcements
Access mess menu information
Manage their profile
👨‍💼 Manager Portal

Managers can:

Access a dedicated manager dashboard
View pending leave requests
Approve or reject leave applications
View approved leaves
View rejected/closed leaves
Manage hostel announcements
Manage mess menu information
🛡️ Admin Portal

Administrators can:

Access an admin dashboard
View an overall hostel overview
Manage users
Manage hostel managers
Monitor leave requests
Manage administrative operations
Access admin-only functionality through role-based authorization
🔐 Authentication & Role-Based Access

The application implements authentication and role-based access for:

Student
Manager
Admin

After authentication, the user's role is checked and the user is redirected to the appropriate dashboard.

                    Login
                      │
                      ▼
               Supabase Auth
                      │
                      ▼
                User Profile
                      │
             ┌────────┼────────┐
             ▼        ▼        ▼
          Student   Manager   Admin
             │        │        │
             ▼        ▼        ▼
         Student    Manager    Admin
         Dashboard  Dashboard  Dashboard
🏗️ System Architecture

HostelMate follows a client-server architecture.

                    ┌──────────────────┐
                    │      User        │
                    └────────┬─────────┘
                             │
                             ▼
                  ┌────────────────────┐
                  │ React Frontend     │
                  │      + Vite        │
                  └─────────┬──────────┘
                            │
                     HTTP / API Calls
                            │
                            ▼
                  ┌────────────────────┐
                  │ Node.js + Express  │
                  │      Backend       │
                  └─────────┬──────────┘
                            │
                    Middleware / APIs
                            │
                            ▼
                  ┌────────────────────┐
                  │     Supabase       │
                  ├────────────────────┤
                  │ Authentication     │
                  │ PostgreSQL         │
                  └────────────────────┘
🛠️ Technology Stack
Frontend
Technology	Purpose
React	Building the user interface
JavaScript	Application logic
JSX	React component structure
React Router	Client-side routing and navigation
CSS	Styling and responsive UI
Vite	Development server and build tool
Backend
Technology	Purpose
Node.js	JavaScript runtime
Express.js	Backend server and API layer
Express Middleware	Request processing and authorization
CORS	Cross-origin communication
dotenv	Environment configuration
Database & Authentication
Technology	Purpose
Supabase	Backend-as-a-service
PostgreSQL	Relational database
Supabase Auth	User authentication
Role-based authorization	Student/Manager/Admin access control
Development Tools
Git
GitHub
VS Code
npm
Vite
📂 Project Structure
SE_Project/
│
├── backend/
│   │
│   ├── middleware/
│   │   └── verifyAdmin.js
│   │
│   ├── routes/
│   │   └── adminRoutes.js
│   │
│   ├── .env
│   ├── createAdmin.js
│   ├── index.js
│   ├── package.json
│   ├── package-lock.json
│   └── supabaseClient.js
│
├── frontend/
│   │
│   ├── public/
│   │   └── images/
│   │
│   ├── src/
│   │   │
│   │   ├── admin/
│   │   │   ├── adminApi.js
│   │   │   ├── AdminDashboard.jsx
│   │   │   ├── AdminLeaves.jsx
│   │   │   ├── AdminManagers.jsx
│   │   │   ├── AdminOverview.jsx
│   │   │   └── AdminUsers.jsx
│   │   │
│   │   ├── auth/
│   │   │   ├── AuthCallback.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── RoleSelect.jsx
│   │   │   ├── SetPassword.jsx
│   │   │   └── VerifyOtp.jsx
│   │   │
│   │   ├── manager/
│   │   │   ├── ApprovedLeaves.jsx
│   │   │   ├── ClosedLeaves.jsx
│   │   │   ├── ManagerAnnouncements.jsx
│   │   │   ├── ManagerDashboard.jsx
│   │   │   ├── ManagerMessMenu.jsx
│   │   │   ├── PendingLeaves.jsx
│   │   │   └── RejectedLeaves.jsx
│   │   │
│   │   ├── student/
│   │   │   ├── ApplyLeave.jsx
│   │   │   ├── LeaveCalendar.jsx
│   │   │   ├── StudentAnnouncements.jsx
│   │   │   ├── StudentDashboard.jsx
│   │   │   ├── StudentMessMenu.jsx
│   │   │   └── StudentProfile.jsx
│   │   │
│   │   ├── components/
│   │   ├── layout/
│   │   │   ├── MainLayout.jsx
│   │   │   └── Sidebar.jsx
│   │   │
│   │   ├── assets/
│   │   ├── styles/
│   │   └── supabase/
│   │
│   ├── package.json
│   ├── vite.config.js
│   └── index.html
│
└── README.md
🔐 Authentication Flow

HostelMate uses Supabase Authentication combined with a user_profiles table for application-level role management.

The authentication flow is approximately:

User
 │
 ▼
Login / Registration
 │
 ▼
Supabase Authentication
 │
 ▼
Authenticated User
 │
 ▼
AuthCallback
 │
 ├── Check authenticated user
 │
 ├── Fetch user profile
 │
 ├── Create profile if required
 │
 ├── Check password status
 │
 └── Determine user role
 │
 ▼
Role-based redirect
 │
 ├── Student  → Student Dashboard
 ├── Manager  → Manager Dashboard
 └── Admin    → Admin Dashboard

The application uses:

supabase.auth.getUser()

to retrieve the authenticated user.

The user's role is then obtained from:

user_profiles
🛡️ Role-Based Authorization

HostelMate distinguishes between authentication and authorization.

Authentication

Determines:

Who is the user?

This is handled using Supabase Authentication.

Authorization

Determines:

What is the user allowed to access?

The application checks the user's role:

student
manager
admin

For example, the admin dashboard verifies that the authenticated user's profile contains:

role = admin

If the user is not authenticated or does not have the required role, access is denied or the user is redirected to the login page.

🔄 Leave Management Workflow

One of the central workflows in HostelMate is leave management.

                 Student
                    │
                    ▼
              Apply for Leave
                    │
                    ▼
             Pending Request
                    │
                    ▼
                 Manager
               /         \
              /           \
             ▼             ▼
         Approve         Reject
            │               │
            ▼               ▼
        Approved         Rejected

The application provides separate views for different leave states, including:

Pending
Approved
Rejected
Closed

This creates a structured workflow instead of relying on manual communication.

🧩 Frontend Architecture

The frontend is organized around role-specific React components.

src/
│
├── auth/
│
├── student/
│
├── manager/
│
├── admin/
│
├── components/
│
├── layout/
│
├── assets/
│
├── styles/
│
└── supabase/
Role-based organization
Student
 ├── Dashboard
 ├── Apply Leave
 ├── Leave Calendar
 ├── Announcements
 ├── Mess Menu
 └── Profile

Manager
 ├── Dashboard
 ├── Pending Leaves
 ├── Approved Leaves
 ├── Rejected Leaves
 ├── Closed Leaves
 ├── Announcements
 └── Mess Menu

Admin
 ├── Overview
 ├── User Directory
 ├── Manage Managers
 └── Leave Monitor
⚛️ React Concepts Used

The project uses several important React concepts.

Functional Components

For example:

export default function AdminDashboard() {
    ...
}
useState

Used for component state:

const [checking, setChecking] = useState(true);
useEffect

Used for operations that need to happen after rendering, such as authentication checks:

useEffect(() => {
    verifyAdmin();
}, [navigate]);
React Router

The application uses:

NavLink
Outlet
useNavigate

for navigation and nested dashboard layouts.

🖥️ Backend Architecture

The backend is built with Node.js and Express.

backend/
│
├── index.js
│
├── routes/
│   └── adminRoutes.js
│
├── middleware/
│   └── verifyAdmin.js
│
└── supabaseClient.js
Entry Point

index.js initializes the Express backend.

Routes

routes/ contains API route definitions.

Middleware

middleware/ contains reusable request-processing and authorization logic.

Supabase Client

supabaseClient.js centralizes the Supabase connection used by the backend.

🗄️ Database

The application uses PostgreSQL through Supabase.

The project works with role-related data including:

user_profiles
manager
admins

The user_profiles table associates an authenticated user with application-level information such as:

id
role
manager_id
std_usn
password_set

This allows the application to keep authentication information and application-specific profile information logically connected.

🔌 API & Data Flow

A typical application request follows this pattern:

React Component
      │
      ▼
API / Supabase Request
      │
      ▼
Express Route
      │
      ▼
Middleware
      │
      ▼
Supabase
      │
      ▼
PostgreSQL
      │
      ▼
Response
      │
      ▼
React State / UI

This separation makes the application easier to organize and maintain.

🔒 Environment Variables

Sensitive configuration is stored using environment variables rather than being hardcoded into the source code.

Example:

SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_key

Never commit your .env file or secret keys to GitHub.

The project uses dotenv on the backend to load environment variables.

🚀 Getting Started
Prerequisites

Make sure you have installed:

Node.js
npm
Git
A Supabase project
1. Clone the repository
git clone <YOUR_REPOSITORY_URL>
cd SE_Project
2. Install backend dependencies
cd backend
npm install

Configure the backend environment variables in:

backend/.env

Then start the backend:

npm start
3. Install frontend dependencies

Open another terminal:

cd frontend
npm install

Start the Vite development server:

npm run dev

Open the local URL provided by Vite.

⚙️ Configuration

Before running the application, configure the required Supabase credentials in the appropriate .env files.
