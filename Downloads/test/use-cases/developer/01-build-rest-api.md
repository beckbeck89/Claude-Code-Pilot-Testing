# Use Case: Build a REST API from Scratch

## Objective

Ask the AI tool to scaffold and build a complete REST API from a brief specification. This tests the tool's ability to generate a full working application with multiple files, proper structure, and production-ready patterns.

## The Task

Build a REST API for a **task management system** with the following requirements:

- **Framework**: FastAPI (Python) or Express (Node.js) — your choice, but use the same for both tools
- **Endpoints**:
  - `GET /tasks` — list all tasks (with filtering by status)
  - `POST /tasks` — create a new task
  - `GET /tasks/{id}` — get a single task
  - `PUT /tasks/{id}` — update a task
  - `DELETE /tasks/{id}` — delete a task
- **Data model**: Task has `id`, `title`, `description`, `status` (todo/in_progress/done), `created_at`, `updated_at`
- **Validation**: Input validation on create/update
- **Storage**: In-memory or SQLite — keep it simple
- **Error handling**: Proper HTTP status codes and error messages

## Acceptance Criteria

- [ ] All 5 endpoints work correctly
- [ ] Input validation rejects bad data with helpful error messages
- [ ] Proper HTTP status codes (201 for create, 404 for not found, etc.)
- [ ] Code is organized across appropriate files (not one giant file)
- [ ] Can be started and tested with curl or similar

## Suggested Prompt

> "Build a REST API for a task management system using [FastAPI/Express]. It needs CRUD endpoints for tasks with fields: id, title, description, status (todo/in_progress/done), created_at, updated_at. Include input validation and proper error handling. Use SQLite for storage."

## What to Observe

- Does it create a proper project structure or dump everything in one file?
- Does it set up the database schema and migrations correctly?
- How does it handle the data model and validation?
- Does it include a way to run and test the API?
- Does it proactively add useful things (CORS, health check, API docs)?
- How many prompts does it take to get a fully working API?
