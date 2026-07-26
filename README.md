# Flask To-Do App

> A minimal, clean to-do list web app built with Flask and server-rendered templates — no JavaScript framework, no database, just the essentials.

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-Web_Framework-000000?logo=flask&logoColor=white)
![HTML](https://img.shields.io/badge/HTML5-Jinja2_Templates-E34F26?logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-Custom_Styling-1572B6?logo=css3&logoColor=white)

## Overview

This project is a compact demonstration of a classic server-rendered web application. Tasks are managed entirely on the server: the Flask backend keeps an in-memory task list, renders it through a Jinja2 template, and every user action (add, complete, delete) is a plain HTTP request followed by a redirect back to the list. It's a clear, readable example of the request → update → redirect → render cycle that underpins traditional web apps.

## Key Features

- **Add tasks** via a simple form (`POST /add`), with empty submissions ignored server-side
- **Toggle completion** — clicking the check mark flips a task between done and not done (`/complete/<id>`), with completed tasks styled distinctly via CSS
- **Delete tasks** with a single click (`/delete/<id>`)
- **Bounds-checked routes** — task IDs are validated before any mutation, so stale links can't crash the app
- **Zero-dependency frontend** — plain HTML rendered with Jinja2 and a small hand-written stylesheet; no client-side JavaScript at all

## Tech Stack

- **Backend:** Python, Flask (routing, redirects, template rendering)
- **Templating:** Jinja2 (`templates/index.html`)
- **Styling:** hand-written CSS (`static/style.css`)
- **Storage:** in-memory Python list (resets on server restart — by design, to keep the example dependency-free)

## Project Structure

```
todo-app/
├── app.py               # Flask app: routes for listing, adding, completing, deleting tasks
├── templates/
│   └── index.html       # Jinja2 template rendering the task list
└── static/
    └── style.css        # Styling, including the completed-task state
```

## Running Locally

Requires Python 3 and pip.

```bash
git clone https://github.com/techieshreya/todo-app.git
cd todo-app

# (optional) create a virtual environment
python -m venv venv
source venv/bin/activate   # on Windows: venv\Scripts\activate

pip install flask
python app.py
```

Then open **http://127.0.0.1:5000** in your browser. The app runs in debug mode, so code changes reload automatically.

## Possible Extensions

- Persist tasks with SQLite (e.g. via `sqlite3` or Flask-SQLAlchemy)
- Add task editing and due dates
- Convert the toggle/delete links to `POST` requests for stricter HTTP semantics
