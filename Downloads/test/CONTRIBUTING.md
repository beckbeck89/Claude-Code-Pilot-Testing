# Contributing to Claudia

Thanks for helping us build a real-world picture of how these AI coding tools compare. Here's how to contribute.

## Submitting an Evaluation

### Option 1: Pull Request (Preferred)

1. **Create a branch** from `main`:
   ```bash
   git checkout -b results/your-name/use-case-name
   ```

2. **Copy the scoring template**:
   ```bash
   cp evaluation-framework/scoring-template.md results/submissions/your-name-use-case.md
   ```

3. **Run the use case** with both Claude Code and GitHub Copilot
   - Follow the instructions in the relevant use case file
   - Fill in the scoring template as you work (capture times, observations, scores)

4. **Submit a PR** to `main` with your completed evaluation

### Option 2: GitHub Issue

If you prefer a lighter-weight submission, open a new issue using the **Evaluation Submission** template. This is great for quick observations or partial evaluations.

## Guidelines for Fair Comparisons

- **Same task, same day**: Run both tools on the same use case in the same session if possible
- **Same starting point**: Begin each tool from the same codebase state
- **Document your setup**: Note tool versions, IDE, extensions, and any relevant config
- **Be specific**: "It struggled with X" is more useful than "it was bad"
- **Include code snippets**: Show what each tool generated — good and bad
- **Note workarounds**: If you had to rephrase a prompt or intervene, record that

## What Makes a Good Submission

- Filled-out scoring template with all 8 metrics rated
- Specific examples and code snippets for notable observations
- Honest assessment — neither tool needs to "win"
- Context about your experience level with the task domain

## PR Review Process

- At least one other team member should review submissions for completeness
- Reviewers check that the scoring template is fully filled out
- Discussion and questions are encouraged in PR comments
- We merge promptly — don't let perfect be the enemy of done

## Adding New Use Cases

Have an idea for a new test case? Great:

1. Create the use case file in the appropriate directory (`use-cases/developer/` or `use-cases/data-science/`)
2. Follow the format of existing use cases (objective, acceptance criteria, what to observe)
3. Submit via PR with a brief explanation of why this use case is valuable

## Code of Conduct

- Be respectful and constructive
- Focus on the tools, not the people who prefer them
- Share honestly — the goal is learning, not advocacy
