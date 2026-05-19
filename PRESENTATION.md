# 📋 PRESENTATION — TaskManager Project

## Slide 1: Title

**TaskManager - Task Management System**

* Student: [Daryn]
* Course Project

---

## Slide 2: Problem

### What problem does the project solve?

❌ Forgotten tasks and deadlines

❌ Lack of centralized planning

❌ Complex project management tools

✅ **Solution:** A simple and user-friendly planner with Telegram bot integration

---

## Slide 3: Technology Stack

### Backend:

* **FastAPI** — modern web framework
* **SQLAlchemy** — ORM for database management
* **Aiogram 3** — asynchronous Telegram Bot API
* **JWT** — secure authentication
* **Matplotlib** — chart generation

### Frontend:

* **Bootstrap 5** — responsive UI
* **Chart.js** — interactive charts
* **JavaScript** — dynamic interface

### Database:

* **SQLite** (development) / **PostgreSQL** (production)

---

## Slide 4: Project Architecture

```plaintext id="5w9lm1"
┌─────────────────────────────────────┐
│     Frontend (Bootstrap + JS)       │
│   - Home, Dashboard, Tasks          │
└──────────────┬──────────────────────┘
               │ HTTP/REST API
┌──────────────▼──────────────────────┐
│        Backend (FastAPI)            │
│   - JWT Authentication              │
│   - CRUD Operations                 │
│   - Chart Generation                │
└──────────────┬──────────────────────┘
               │
    ┌──────────┴──────────┐
    ▼                     ▼
┌─────────┐         ┌──────────────┐
│Database │         │Telegram Bot  │
│SQLite   │         │(Aiogram)     │
└─────────┘         └──────────────┘
```

---

## Slide 5: Features — Telegram Bot

### Commands:

* `/start` — Registration and welcome message
* `/add` — Step-by-step task creation
* `/list` — List of all tasks with buttons
* `/pending` — Active tasks
* `/completed` — Completed tasks
* `/stats` — Text statistics
* `/charts` — **Charts (Matplotlib)** 📊
* `/help` — Help information

### Features:

✅ Interactive buttons (InlineKeyboard)

✅ FSM (Finite State Machine) for task creation

✅ Priorities: High / Medium / Low

✅ Automatic reminders (optional)

---

## Slide 6: Features — Web Interface

### Pages:

1. **Home** — Landing page with project description
2. **Login/Register** — JWT authentication
3. **Dashboard** — Statistics and charts
4. **Tasks** — CRUD operations

### Capabilities:

✅ Create/edit/delete tasks

✅ Categories and tags

✅ Filtering (status, priority, category)

✅ Deadline management

✅ Interactive charts (Chart.js)

✅ Responsive design (mobile devices)

---

## Slide 7: Charts and Analytics

### In Telegram (Matplotlib):

### Statistics Dashboard:

* 🥧 Pie chart of task statuses
* 📊 Bar chart of priorities
* 📈 Weekly productivity graph
* 🏷️ Top categories chart

### On the Website (Chart.js):

### Interactive Charts:

* Doughnut chart — task distribution
* Line chart — completion dynamics
* Bar chart — tasks by category
* Real-time updates

---

## Slide 8: Database (ER Diagram)

```plaintext id="9vx9m2"
┌──────────────┐      ┌────────────────┐      ┌─────────────┐
│    Users     │      │     Tasks      │      │  Comments   │
├──────────────┤      ├────────────────┤      ├─────────────┤
│ telegram_id  │──┐   │ id             │   ┌──│ id          │
│ username     │  │   │ telegram_id    │───┘  │ task_id     │
│ first_name   │  └───│ title          │      │ text        │
│ created_at   │      │ description    │      │ created_at  │
└──────────────┘      │ priority       │      └─────────────┘
                      │ status         │
┌──────────────┐      │ category       │
│  WebUsers    │      │ tags           │
├──────────────┤      │ deadline       │
│ id           │──────│ created_at     │
│ email        │      │ completed_at   │
│ password_hash│      └────────────────┘
│ telegram_id  │
└──────────────┘
```

### Tables:

* `users` — Telegram users
* `web_users` — web application users
* `tasks` — tasks with categories and tags
* `comments` — task comments

---

## Slide 9: Requirement Coverage

### ✅ Stage 1 (30%):

* Console application (Telegram bot)
* Basic CRUD operations
* Database storage
* Data types and functions

### ✅ Stage 2 (60%):

* Web application (FastAPI)
* OOP models (User, Task, Comment)
* CRUD via web interface
* **Advanced module:** Telegram API integration

### ✅ Stage 3 (100%):

* Categories, tags, filters
* **Visualization:** Chart.js + Matplotlib
* Task comments
* **JWT authentication**
* **Bootstrap frontend**
* Deployment-ready (Docker)

---

## Slide 10: Unique Features

### 🎯 What makes the project unique:

1. **Two interfaces** — Web + Telegram
2. **Synchronization** — tasks available everywhere
3. **Dual visualization:**

   * Static charts (Matplotlib) → Telegram
   * Interactive charts (Chart.js) → Web
4. **Modern tech stack** — FastAPI, async/await

---

## Slide 11: API Documentation

### FastAPI Automatic Documentation:

**Swagger UI:** `http://localhost:8000/docs`

### Endpoints:

```plaintext id="5l9xx4"
POST   /api/auth/register         - Register
POST   /api/auth/login            - Login (JWT)
GET    /api/auth/me               - Current user

GET    /api/tasks                 - Get tasks
POST   /api/tasks                 - Create task
PATCH  /api/tasks/{id}/complete   - Complete task
DELETE /api/tasks/{id}            - Delete task

GET    /api/statistics            - Statistics
```

---

## Slide 12: Deployment (Production)

### Deployment Options:

### 1. Railway.app (recommended)

```bash id="rjz17s"
# Connect GitHub → Auto-deploy
```

### 2. Docker

```bash id="r9xx6d"
docker-compose up -d
```

### 3. VPS (DigitalOcean, AWS)

```bash id="h5ymx8"
uvicorn main:app --host 0.0.0.0 --port 8000
```

### CI/CD:

GitHub Actions for automatic deployment

---

## Slide 13: Demonstration

### Demo Scenario:

### 1. Telegram Bot:

* Create a task using `/add`
* View tasks using `/list`
* Mark task as completed
* Generate charts using `/charts`

### 2. Web Interface:

* Registration → Login
* Dashboard with charts
* Create task with category
* Filter tasks

### 3. Synchronization:

* Show that a task created in the bot appears on the website

---

## Slide 14: Project Metrics

### 📊 Code Statistics:

* **Lines of code:** ~2000+
* **Python files:** 7
* **HTML files:** 4
* **API endpoints:** 10+
* **Database tables:** 4
* **Telegram commands:** 8

### 🛠️ Technologies:

* Languages: Python, JavaScript, HTML/CSS
* Frameworks: FastAPI, Bootstrap
* Libraries: 15+
* Patterns: MVC, REST API, JWT

---

## Slide 15: Future Development

### 🚀 Planned Features:

* [ ] Email deadline notifications
* [ ] Export tasks to PDF/Excel
* [ ] Telegram Web App (mini app)
* [ ] Recurring tasks (cron jobs)
* [ ] Team collaboration projects
* [ ] Mobile application (React Native)
* [ ] AI assistant for prioritization
* [ ] Google Calendar integration

---

## Slide 16: Conclusion

### ✅ Achievements:

1. **Full-featured application** — Web + Bot
2. **Modern technology stack** — FastAPI, async
3. **Beautiful UI** — Bootstrap, responsive design
4. **Data visualization** — 2 chart libraries
5. **Production-ready** — Docker, JWT, deployment
6. **Documentation** — README, API docs

### 🎯 Applications:

* Personal planning
* Small team project management
* Educational tasks
* Workflow organization

---

## Slide 17: Thank You!

## Questions? 🙋‍♂️

---

# BONUS: Answers to Possible Questions

### Q: Why FastAPI instead of Django?

**A:** FastAPI is more modern, faster, supports async/await natively, and automatically generates API documentation.

### Q: Why use two chart libraries?

**A:** Matplotlib is used for static images in Telegram, while Chart.js provides interactive charts on the website.

### Q: How can the project scale?

**A:** PostgreSQL instead of SQLite, Redis for caching, and Kubernetes for orchestration.

### Q: What about security?

**A:** JWT tokens, password hashing with bcrypt, SQL injection protection via ORM, and HTTPS in production.

### Q: Are there tests?

**A:** pytest can be added for unit and integration testing.
