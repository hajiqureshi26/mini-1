# DevOps Task Manager

A beginner-friendly Flask + SQLite CRUD application for DevOps practice.

## Features
- Add task records (insert)
- List and retrieve saved tasks
- Mark tasks completed (update)
- Delete tasks
- SQLite persistence
- `/health` health endpoint
- Docker image and persistent named volume support

## Run locally (Windows PowerShell)
```powershell
python -m venv venv
venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```
Open http://localhost:5000

Health check: http://localhost:5000/health

## Run with Docker
```powershell
docker build -t devops-task-manager:1.0 .
docker run -d --name task-manager -p 5000:5000 -v task-manager-data:/data devops-task-manager:1.0
```

Check:
```powershell
docker ps
docker logs task-manager
curl http://localhost:5000/health
```

Database file is `tasks.db` locally, and `/data/tasks.db` in the Docker container. The named Docker volume preserves data across container recreation.

## Stop and remove container (volume retained)
```powershell
docker stop task-manager
docker rm task-manager
```
