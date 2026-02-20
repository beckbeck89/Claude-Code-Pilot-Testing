# Evaluation: Build a REST API

## Evaluator Info

- **Name**: Alex Demo
- **Date**: 2025-02-15
- **Use Case**: [01 - Build REST API](../../use-cases/developer/01-build-rest-api.md)
- **Domain**: Developer

## Setup

- **Claude Code version**: 1.0.5
- **Copilot version/tier**: Copilot Business (GPT-4)
- **IDE**: VS Code 1.96
- **Language/Framework**: Python / FastAPI
- **OS**: macOS 15.2
- **Relevant extensions/plugins**: Python, Pylance, GitHub Copilot, Claude Code CLI

## Task Description

Built a task management REST API with CRUD endpoints, SQLite storage, and input validation following the use case spec.

## Scorecard

| Metric | Claude Code (1-5) | Copilot (1-5) | Notes |
|--------|-------------------|---------------|-------|
| Speed | 4 | 3 | Claude scaffolded the full project in one shot; Copilot needed file-by-file prompting |
| Accuracy | 4 | 3 | Both had minor issues, but Claude's code ran on first try |
| Code Quality | 4 | 4 | Both produced clean, idiomatic FastAPI code |
| Context Understanding | 5 | 2 | Claude understood multi-file structure; Copilot focused on current file only |
| Iteration Efficiency | 4 | 3 | 3 prompts with Claude vs 8 with Copilot to reach the same result |
| Autonomy | 5 | 2 | Claude set up the DB, created all files, and ran the server; Copilot needed guidance per step |
| Scope of Capability | 5 | 3 | Claude created project structure, installed deps, ran tests; Copilot only generated code |
| Domain Fit | 3 | 4 | Copilot's inline suggestions were faster for small edits during iteration |
| **Total** | **34/40** | **24/40** | |

## Timing

| Measurement | Claude Code | Copilot |
|-------------|-------------|---------|
| Time to first useful output | 45 seconds | 30 seconds |
| Total time to completion | 8 minutes | 22 minutes |
| Number of prompts/interactions | 3 | 8 |

## Detailed Observations

### Claude Code

**What worked well:**

- Generated a complete project structure in one prompt (main.py, models.py, database.py, schemas.py)
- Set up SQLAlchemy models and Pydantic schemas correctly
- Ran `pip install` and started the server automatically
- Proactively added CORS middleware and a health check endpoint

**What didn't work well:**

- Initially used an older SQLAlchemy session pattern (fixed on second prompt)
- Didn't add any API documentation beyond the auto-generated Swagger

**Notable code snippet (good):**

```python
# Clean separation of concerns — generated in one shot
# database.py
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker, declarative_base

SQLALCHEMY_DATABASE_URL = "sqlite:///./tasks.db"
engine = create_engine(SQLALCHEMY_DATABASE_URL, connect_args={"check_same_thread": False})
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)
Base = declarative_base()
```

### GitHub Copilot

**What worked well:**

- Inline completions were fast and accurate for individual functions
- Good at suggesting Pydantic model fields based on variable names
- Autocomplete for FastAPI decorators was very smooth

**What didn't work well:**

- Couldn't scaffold the full project — needed file-by-file prompting
- Suggestions were limited to the current file context
- Didn't set up the database or run any commands
- Required manual wiring of routes, database sessions, and error handlers

**Notable code snippet (needed correction):**

```python
# Copilot suggested this — missing the status filter from the spec
@app.get("/tasks")
async def get_tasks():
    tasks = db.query(Task).all()
    return tasks
# Had to manually prompt for the status filter parameter
```

## Head-to-Head Comparison

For this full-project scaffolding task, Claude Code was significantly more effective. Its ability to create multiple files, understand the full project structure, and execute terminal commands meant the API was running in under 10 minutes with minimal intervention. Copilot produced equally good code at the individual function level, but couldn't orchestrate the full project.

## Key Takeaways

- Claude Code excels at "build from scratch" tasks where multi-file coordination and terminal access matter
- Copilot excels at in-editor, inline assistance during active coding
- They're not strictly competing — they serve different workflow moments
- For this type of task, Claude Code saved about 14 minutes of manual wiring and setup
