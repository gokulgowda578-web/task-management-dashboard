# TaskFlow — Task Management Dashboard

A full-stack task management web application inspired by Trello, Asana, and Jira. Built with React, Node.js, Express, and MySQL. Includes JWT authentication, project & task CRUD, a drag-and-drop Kanban board, dashboard analytics with Chart.js, filtering/search, and full dark mode support.

![Tech](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=black)
![Tech](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js&logoColor=white)
![Tech](https://img.shields.io/badge/MySQL-database-4479A1?logo=mysql&logoColor=white)
![Tech](https://img.shields.io/badge/Tailwind-CSS-38B2AC?logo=tailwindcss&logoColor=white)

## ✨ Features

- **Authentication** — Register, login, JWT-based sessions, bcrypt password hashing
- **Dashboard** — Stat cards (total/pending/in-progress/completed), task status doughnut chart, 7-day productivity line chart, recent tasks
- **Tasks** — Create, edit, delete, mark complete, filter by status/priority, search by title/description
- **Kanban Board** — Drag-and-drop tasks between Todo / In Progress / Completed columns
- **Projects** — Create/update/delete projects, view task count & completion percentage per project
- **Profile** — View account details, join date, and personal task statistics
- **UI/UX** — Responsive layout, sticky sidebar, dark mode toggle, soft shadows, rounded cards, smooth hover transitions, Inter font

## 🏗️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React, React Router DOM, Axios, Tailwind CSS, Chart.js (react-chartjs-2), Vite |
| Backend | Node.js, Express.js, MVC architecture |
| Database | MongoDB (Mongoose) |
| Auth | JWT, bcryptjs |

## 📁 Project Structure

```
task-management-dashboard/
├── frontend/
│   ├── src/
│   │   ├── components/   # Layout, TaskModal, ProjectModal
│   │   ├── pages/         # Login, Register, Dashboard, Tasks, Projects, Kanban, Profile
│   │   ├── services/       # api.js (axios instance + endpoints)
│   │   ├── context/        # AuthContext, ThemeContext
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
├── backend/
│   ├── config/db.js          # Mongoose connection
│   ├── models/                # User, Project, Task schemas
│   ├── controllers/           # authController, taskController, projectController
│   ├── routes/                  # authRoutes, taskRoutes, projectRoutes
│   ├── middleware/              # auth, validation, errorHandler
│   ├── seed/seed.js             # sample data seeder
│   ├── server.js
│   └── package.json
└── README.md
```

## 🚀 Getting Started (Local Development)

### Prerequisites

- Node.js 18+
- MongoDB 6+ (local install, or a free cluster on [MongoDB Atlas](https://www.mongodb.com/atlas))

### 1. Backend setup

```bash
cd backend
cp .env.example .env
# edit .env — set MONGO_URI (e.g. mongodb://localhost:27017/taskmanager
#              or your Atlas connection string) and a strong JWT_SECRET
npm install
npm run dev      # starts on http://localhost:5000
```

### 2. Seed sample data (optional)

```bash
npm run seed
```

This clears and populates the database with 2 demo users, 4 projects, and 12 tasks.

> Demo login: `alex@example.com` / `password123` (or just register a fresh account).

### 3. Frontend setup

```bash
cd frontend
cp .env.example .env
# VITE_API_URL=http://localhost:5000/api
npm install
npm run dev       # starts on http://localhost:5173
```

Open `http://localhost:5173` in your browser, register a new account, and start managing tasks!

## 🔌 API Reference

All `/api/tasks` and `/api/projects` routes require an `Authorization: Bearer <token>` header.

### Auth

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register a new user (`name`, `email`, `password`) |
| POST | `/api/auth/login` | Login (`email`, `password`) → returns JWT + user |
| GET | `/api/auth/profile` | Get current user profile + task stats |

### Tasks

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/tasks` | List tasks (supports `?status=&priority=&search=&sort=&order=`) |
| GET | `/api/tasks/stats` | Dashboard stats: totals by status, recent tasks, 7-day chart data |
| GET | `/api/tasks/:id` | Get single task |
| POST | `/api/tasks` | Create task (`title`, `description`, `priority`, `status`, `due_date`, `project_id`) |
| PUT | `/api/tasks/:id` | Update task |
| DELETE | `/api/tasks/:id` | Delete task |

### Projects

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/projects` | List projects with task count & completion % |
| POST | `/api/projects` | Create project (`project_name`, `description`) |
| PUT | `/api/projects/:id` | Update project |
| DELETE | `/api/projects/:id` | Delete project |

## 🎨 Design

- **Primary:** `#4F46E5` · **Secondary:** `#6366F1` · **Success:** `#22C55E` · **Warning:** `#F59E0B` · **Danger:** `#EF4444`
- **Font:** Inter
- Light & dark themes via Tailwind's `class` strategy, toggle persisted in `localStorage`

## 📦 Deployment

See [DEPLOYMENT.md](./DEPLOYMENT.md) for step-by-step instructions to deploy:
- Frontend → Vercel
- Backend → Render
- Database → MongoDB Atlas

## 📄 License

MIT — free to use for portfolio, learning, and internship submissions.
