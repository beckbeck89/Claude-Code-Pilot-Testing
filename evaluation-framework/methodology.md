# Evaluation Methodology

How to run a fair, repeatable comparison between Claude Code and GitHub Copilot.

## Principles

1. **Same task, same conditions**: Both tools should be tested on the exact same task with the same starting point
2. **Document everything**: Record setup, prompts, timing, and outputs
3. **Be honest**: Neither tool needs to "win" — we're learning, not advocating
4. **Use realistic tasks**: Test on work you'd actually do, not toy examples

## Step-by-Step Process

### Before You Start

1. **Choose a use case** from `use-cases/developer/` or `use-cases/data-science/`
2. **Read the use case file** completely — note the acceptance criteria
3. **Prepare your environment**: Same project, same machine, same state
4. **Copy the [scoring template](scoring-template.md)** to `results/submissions/your-name-use-case.md`
5. **Clear your IDE state**: Close other projects, reset any cached contexts

### Running the Evaluation

1. **Start with Tool A** (alternate which tool goes first across evaluations to reduce order bias)
2. **Start a timer** when you begin your first prompt
3. **Work naturally** — don't try to game prompts for one tool or the other
4. **Record as you go**:
   - Timestamp key moments (first useful output, major breakthroughs, blockers)
   - Count prompts/interactions
   - Screenshot or copy notable outputs (good and bad)
5. **Stop the timer** when you reach a working solution or give up
6. **Reset your workspace** to the same starting state
7. **Repeat with Tool B**

### After Both Runs

1. **Score each metric** using the [1-5 scale](metrics.md)
2. **Write your observations** — be specific with examples
3. **Identify the winner per-metric**, not just overall
4. **Note any tasks where one tool simply couldn't do what the other could**

## Controlling for Bias

- **Alternate order**: If you always start with Claude Code, you'll have fresher context by the time you use Copilot (or vice versa). Alternate.
- **Don't carry knowledge**: After using Tool A, try not to use what you learned about the problem when testing Tool B. If you can't avoid this, note it.
- **Use the same prompts**: When possible, give both tools the same initial prompt. Record any rephrasing you needed.
- **Separate sessions**: Don't run both tools simultaneously — give each your full attention.

## What Counts as "Complete"?

A task is complete when:
- The code runs without errors
- It meets the acceptance criteria in the use case file
- You'd be comfortable shipping it (or using it in an analysis)

If you can't reach completion with one tool, that's a valid result — document where you got stuck and how far the tool took you.

## Partial Evaluations

Not every evaluation needs to be exhaustive. You can submit:
- **Full evaluation**: Complete scoring template with all metrics
- **Quick take**: Just the scorecard and a paragraph of observations (use the GitHub issue template)
- **Specific finding**: A single notable observation about one tool on one task

All contributions are valuable. Don't let the template intimidate you.
