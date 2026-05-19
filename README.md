# 📋 TaskManager - Task Management System

A full-featured web service for task management with Telegram bot integration, charts, and analytics.

## 🎯 Project Description

TaskManager is a modern web application for planning and tracking tasks that includes:

* 🌐 Web interface built with FastAPI + Bootstrap
* 📱 Telegram bot for quick task management
* 📊 Charts and analytics (Chart.js + Matplotlib)
* 🔐 JWT authentication
* 🏷️ Categories, tags, and filters
* ⏰ Deadlines and priorities

## 🏗️ Project Architecture

```plaintext
task-manager/
├── backend/
│   ├── database.py       # SQLAlchemy models (User, Task, Comment)
│   ├── crud.py           # Database CRUD operations
│   ├── auth.py           # JWT authentication
│   ├── models.py         # Pydantic schemas for API
│   ├── main.py           # FastAPI application
│   ├── bot.py            # Telegram bot (aiogram)
│   └── charts.py         # Matplotlib charts
│
├── frontend/
│   ├── static/
│   │   └── css/style.css
│   └── templates/
│       ├── index.html       # Home page
│       ├── login.html       # Login/Register
│       ├── dashboard.html   # Dashboard with charts
│       └── tasks.html       # Task management
│
├── .env                  # Environment variables
├── requirements.txt      # Dependencies
├── tasks.db              # SQLite database
└── README.md
```

## 📦 Technology Stack

### Backend:

* **FastAPI** — web framework
* **SQLAlchemy** — ORM for database operations
* **Aiogram 3** — Telegram Bot API
* **JWT** (python-jose) — authentication
* **Matplotlib** — chart generation
* **Uvicorn** — ASGI server

### Frontend:

* **Bootstrap 5** — UI framework
* **Chart.js** — interactive charts
* **Vanilla JavaScript** — frontend logic

### Database:

* **SQLite** — for development
* **PostgreSQL** — for production (optional)

## 🚀 Installation and Setup

### 1. Clone the Project

```bash
git clone <your-repo>
cd task-manager
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure the `.env` File

Create a `.env` file in the project root:

```env
BOT_TOKEN=your_telegram_bot_token_here
SECRET_KEY=your-secret-key-for-jwt
```

### How to Get a BOT_TOKEN:

1. Open Telegram
2. Search for @BotFather
3. Send `/newbot`
4. Follow the instructions
5. Copy the token into `.env`

### 4. Run the Telegram Bot

```bash
cd backend
python bot.py
```

The bot will now be available in Telegram.

### 5. Run the Web Server

Open a new terminal:

```bash
cd backend
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

The web interface will be available at:

```plaintext
http://localhost:8000
```

## 📱 Using the Telegram Bot

### Bot Commands:

* `/start` — Start using the bot and register
* `/add` — Add a new task step by step
* `/list` — Show all tasks
* `/pending` — Show active tasks
* `/completed` — Show completed tasks
* `/stats` — Display text statistics
* `/charts` — Generate statistics charts (Matplotlib)
* `/help` — Show help information

### Example Usage:

```plaintext
You: /add
Bot: Enter the task title
You: Buy milk
Bot: Enter a description (or - to skip)
You: At the local store
Bot: Choose a priority:
     [🔴 High] [🟡 Medium] [🟢 Low]
You: *clicks 🟡*
Bot: ✅ Task #1 created!
```

## 🌐 Web Interface

### Pages:

1. **Home** (`/`) — Landing page with project description
2. **Login/Register** (`/login`) — Authentication page
3. **Dashboard** (`/dashboard`) — Statistics and charts
4. **Tasks** (`/tasks`) — Task management

### Web Features:

* ✅ Create, edit, and delete tasks
* 🏷️ Categories and tags
* 🔍 Filtering by status, priority, and category
* 📊 Interactive charts (Chart.js)
* ⏰ Deadline management
* 💬 Task comments (optional)

## 🔐 Authentication

### Registration:

1. Open `/login`
2. Select the “Register” tab
3. Fill in the form (email, password, first name)
4. Optionally provide your Telegram ID for synchronization

### Login:

1. Enter your email and password
2. Receive a JWT token
3. The token is stored in localStorage

### Telegram Integration:

During registration, users can provide their Telegram ID (via @userinfobot) so tasks can sync between the Telegram bot and the web application.

## 📊 Charts and Analytics

### In Telegram (Matplotlib):

The `/charts` command generates a PNG image with 4 charts:

* Pie chart for task statuses
* Bar chart for priorities
* Productivity line graph
* Top categories chart

### In the Web Interface (Chart.js):

Interactive charts on the dashboard:

* Task status chart (doughnut)
* Weekly productivity chart (line)
* Tasks by category chart (bar)
* Real-time updates

## 🗄️ Database Structure

### `users` Table:

```sql
- telegram_id (INT, PRIMARY KEY)
- username (VARCHAR)
- first_name (VARCHAR)
- created_at (DATETIME)
```

### `web_users` Table:

```sql
- id (INT, PRIMARY KEY)
- email (VARCHAR, UNIQUE)
- password_hash (VARCHAR)
- first_name (VARCHAR)
- telegram_id (INT, UNIQUE, NULLABLE)
- created_at (DATETIME)
```

### `tasks` Table:

```sql
- id (INT, PRIMARY KEY)
- telegram_id (INT)
- title (VARCHAR)
- description (TEXT)
- priority (ENUM: low, medium, high)
- status (ENUM: pending, completed, cancelled)
- category (VARCHAR)
- tags (VARCHAR)
- deadline (DATETIME)
- created_at (DATETIME)
- completed_at (DATETIME)
```

### `comments` Table:

```sql
- id (INT, PRIMARY KEY)
- task_id (INT)
- telegram_id (INT)
- text (TEXT)
- created_at (DATETIME)
```

## 🔧 API Endpoints

### Authentication:

* `POST /api/auth/register` — Register
* `POST /api/auth/login` — Login (get JWT token)
* `GET /api/auth/me` — Get current user info

### Tasks:

* `GET /api/tasks` — Get all tasks
* `POST /api/tasks` — Create a task
* `GET /api/tasks/{id}` — Get task by ID
* `PATCH /api/tasks/{id}/complete` — Mark task as completed
* `DELETE /api/tasks/{id}` — Delete a task

### Statistics:

* `GET /api/statistics` — Get full statistics and charts

## 🎓 Project Requirements Coverage

### Stage 1 (30%): ✅ COMPLETED

* ✅ Console application (Telegram bot)
* ✅ Basic operations: add/delete/complete tasks
* ✅ Database integration (SQLite)
* ✅ Functions and data types usage

### Stage 2 (60%): ✅ COMPLETED

* ✅ Web application (FastAPI)
* ✅ OOP models (Task, User, Comment)
* ✅ CRUD operations through web interface
* ✅ Advanced module: Telegram API integration

### Stage 3 (100%): ✅ COMPLETED

* ✅ Categories, tags, and filters
* ✅ Data visualization (Chart.js + Matplotlib)
* ✅ Task comments
* ✅ JWT authentication
* ✅ Modern UI (Bootstrap)
* ✅ Ready for deployment

## 🚀 Deployment (Production)

### Option 1: Railway.app

1. Create an account on Railway
2. Connect your GitHub repository
3. Configure environment variables
4. Deploy automatically

### Option 2: Render.com

1. Create a Web Service
2. Set the start command:

```bash
uvicorn backend.main:app --host 0.0.0.0 --port $PORT
```

3. Add environment variables
4. Deploy

### Option 3: VPS (DigitalOcean, AWS, etc.)

```bash
# Install dependencies
pip install -r requirements.txt

# Run with gunicorn
gunicorn backend.main:app -w 4 -k uvicorn.workers.UvicornWorker --bind 0.0.0.0:8000

```

## 📝 TODO (Future Improvements)

* [ ] Email notifications for deadlines
* [ ] Export tasks to PDF/Excel
* [ ] Telegram Web App support
* [ ] Recurring tasks (cron jobs)
* [ ] Shared tasks (multi-user collaboration)
* [ ] File attachments for tasks
* [ ] Dark mode
* [ ] Mobile application
