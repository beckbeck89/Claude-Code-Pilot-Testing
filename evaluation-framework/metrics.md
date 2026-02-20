# Evaluation Metrics

We evaluate Claude Code and GitHub Copilot across **8 dimensions**. Each metric is scored on a **1-5 scale**.

## Scoring Scale

| Score | Meaning |
|-------|---------|
| 1 | Poor — significant issues, major manual intervention needed |
| 2 | Below Average — noticeable gaps, frequent corrections required |
| 3 | Adequate — gets the job done with some adjustments |
| 4 | Good — minor issues only, mostly production-ready |
| 5 | Excellent — impressive output, minimal or no corrections needed |

---

## 1. Speed

**What it measures**: How quickly the tool produces useful output.

| Sub-metric | How to Measure |
|------------|---------------|
| Time to first useful output | Start timer when you submit the prompt, stop when you get code you can work with |
| Time to task completion | Total elapsed time from start to a working solution |

**Tips**: Use a stopwatch or note timestamps. "Useful output" means code that compiles/runs, not just any text.

---

## 2. Accuracy

**What it measures**: Correctness of the generated code.

| Sub-metric | How to Measure |
|------------|---------------|
| Runs without errors | Does the code execute on first try? |
| Passes tests | Does it pass existing or generated test cases? |
| Logical correctness | Does it actually solve the stated problem? |
| Edge case handling | Does it handle boundary conditions and edge cases? |

**Tips**: Run the code. Don't just eyeball it. Note any errors and what it took to fix them.

---

## 3. Code Quality

**What it measures**: How well-written and maintainable the code is.

| Sub-metric | How to Measure |
|------------|---------------|
| Readability | Clear variable names, logical structure, appropriate comments |
| Best practices | Follows language idioms, design patterns, and conventions |
| Maintainability | Would you be comfortable handing this to a teammate? |
| Security | No obvious vulnerabilities (SQL injection, XSS, secrets in code) |

**Tips**: Would this pass your team's code review? That's a good bar.

---

## 4. Context Understanding

**What it measures**: How well the tool understands the broader project.

| Sub-metric | How to Measure |
|------------|---------------|
| Project structure awareness | Does it understand the repo layout and file relationships? |
| Existing code integration | Does it match the style and patterns already in the codebase? |
| Requirement comprehension | Does it address the full intent of your request, not just the literal words? |
| Multi-file awareness | Can it reason about and modify multiple related files? |

**Tips**: This is where the tools often differ the most. Pay close attention to whether the tool "gets" your project.

---

## 5. Iteration Efficiency

**What it measures**: How many rounds of interaction are needed to reach a good result.

| Sub-metric | How to Measure |
|------------|---------------|
| Prompts to completion | Count total prompts/messages sent before the task is done |
| Rephrasing needed | How often did you need to rephrase or clarify your request? |
| Progressive improvement | Does each iteration meaningfully improve the output? |

**Tips**: Keep a tally. Fewer rounds = better efficiency. Note if you had to completely restart.

---

## 6. Autonomy

**What it measures**: How independently the tool can work.

| Sub-metric | How to Measure |
|------------|---------------|
| Self-direction | Can it break down a vague request into concrete steps? |
| Error recovery | When something fails, does it diagnose and fix the issue? |
| Proactive suggestions | Does it identify issues or improvements you didn't ask about? |
| Tool usage | Does it effectively use available tools (terminal, file system, browser)? |

**Tips**: Try giving a high-level instruction and see how far each tool gets on its own.

---

## 7. Scope of Capability

**What it measures**: The range of tasks the tool can handle.

| Sub-metric | How to Measure |
|------------|---------------|
| Multi-file edits | Can it coordinate changes across multiple files? |
| Terminal/CLI operations | Can it run commands, install packages, manage environments? |
| Language breadth | How well does it handle your specific language/framework? |
| Non-code tasks | Can it help with docs, configs, CI/CD, architecture decisions? |

**Tips**: Note any tasks where one tool simply can't do what the other can.

---

## 8. Domain Fit

**What it measures**: How well-suited the tool is for the specific task domain.

### For Developer Tasks

| Sub-metric | How to Measure |
|------------|---------------|
| Framework knowledge | Does it know the APIs and patterns of your framework? |
| Debugging capability | Can it effectively diagnose and fix bugs? |
| Architecture sense | Does it suggest sound architectural decisions? |

### For Data Science Tasks

| Sub-metric | How to Measure |
|------------|---------------|
| Statistical correctness | Are statistical methods applied correctly? |
| Visualization quality | Are charts well-designed and informative? |
| Notebook workflow | Does it work well with Jupyter notebooks? |
| Library knowledge | Does it know pandas, sklearn, matplotlib, etc. well? |

---

## Aggregating Scores

For each evaluation, you'll produce a scorecard like this:

| Metric | Claude Code | Copilot | Notes |
|--------|-------------|---------|-------|
| Speed | /5 | /5 | |
| Accuracy | /5 | /5 | |
| Code Quality | /5 | /5 | |
| Context Understanding | /5 | /5 | |
| Iteration Efficiency | /5 | /5 | |
| Autonomy | /5 | /5 | |
| Scope of Capability | /5 | /5 | |
| Domain Fit | /5 | /5 | |
| **Total** | **/40** | **/40** | |

The total score is informative, but the per-metric breakdown is where the real insights are. A tool that scores 5 on Autonomy but 2 on Speed tells a very different story than one that's 3 across the board.
