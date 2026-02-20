# Use Case: Debug Existing Code

## Objective

Give the AI tool a codebase with several intentional bugs and ask it to find and fix them. This tests diagnostic ability, code comprehension, and how well the tool reasons about runtime behavior.

## The Task

Use the following buggy Python script (or create your own equivalent). The code is a simple data processing pipeline that reads a CSV, transforms data, and outputs a summary. It has **5 intentional bugs** of varying difficulty.

```python
import csv
from collections import defaultdict
from datetime import datetime

def load_transactions(filepath):
    """Load transactions from CSV file."""
    transactions = []
    with open(filepath, 'r') as f:
        reader = csv.DictReader(f)
        for row in reader:
            row['amount'] = float(row['amount'])
            row['date'] = datetime.strptime(row['date'], '%Y-%m-%d')
            transactions.append(row)
    return transactions

def filter_by_date_range(transactions, start_date, end_date):
    """Filter transactions within a date range (inclusive)."""
    return [t for t in transactions if start_date < t['date'] < end_date]  # Bug 1: should be <= on both sides

def calculate_totals_by_category(transactions):
    """Calculate total amount per category."""
    totals = {}
    for t in transactions:
        category = t['category']
        totals[category] = t['amount']  # Bug 2: should be += not =
    return totals

def find_largest_transaction(transactions):
    """Find the transaction with the largest amount."""
    if not transactions:
        return None
    largest = transactions[0]
    for t in transactions:
        if t['amount'] > largest:  # Bug 3: comparing to dict not amount
            largest = t
    return largest

def generate_summary(transactions):
    """Generate a summary report."""
    totals = calculate_totals_by_category(transactions)
    largest = find_largest_transaction(transactions)

    summary = {
        'total_transactions': len(transactions),
        'total_amount': sum(t['amount'] for t in transactions),
        'categories': totals,
        'largest_transaction': largest,
        'average_amount': sum(t['amount'] for t in transactions) / len(transactions)  # Bug 4: no zero division guard
    }
    return summary

def format_report(summary):
    """Format summary as readable text."""
    lines = []
    lines.append(f"Transaction Report")
    lines.append(f"Total: {summary['total_transactions']} transactions")
    lines.append(f"Sum: ${summary['total_amount']:.2f}")
    lines.append(f"Average: ${summary['average_amount']:.2f}")
    lines.append(f"\nBy Category:")
    for cat, amount in summary['categories'].items():
        lines.append(f"  {cat}: ${amount:.2f}")
    lines.append(f"\nLargest: {summary['largest_transaction']['title']}")  # Bug 5: key might not exist if no transactions
    return '\n'.join(lines)

if __name__ == '__main__':
    transactions = load_transactions('transactions.csv')
    filtered = filter_by_date_range(transactions, datetime(2024, 1, 1), datetime(2024, 12, 31))
    summary = generate_summary(filtered)
    print(format_report(summary))
```

## Acceptance Criteria

- [ ] Tool identifies at least 4 of the 5 bugs
- [ ] Tool explains why each bug causes incorrect behavior
- [ ] Fixes are correct and don't introduce new bugs
- [ ] Tool suggests or runs tests to verify the fixes

## Suggested Prompt

> "This code has several bugs. Can you find and fix them? Explain what each bug does wrong."

## What to Observe

- Does it find all 5 bugs or miss some?
- Does it explain the root cause or just patch symptoms?
- Does it read the whole file before making changes?
- Does it suggest testing the fixes?
- How does it handle the subtle bugs vs. the obvious ones?
- Does it spot any additional issues beyond the 5 intentional ones?
