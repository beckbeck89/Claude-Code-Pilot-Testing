# Use Case: Write Tests

## Objective

Ask the AI tool to generate comprehensive tests for existing code. Tests the tool's ability to understand code behavior, identify edge cases, and produce well-structured test suites.

## The Task

Write tests for the following utility module:

```python
from datetime import datetime, timedelta
from typing import Optional


def parse_duration(duration_str: str) -> timedelta:
    """Parse a human-readable duration string into a timedelta.

    Supported formats: '30s', '5m', '2h', '1d', '1h30m', '2d12h'
    """
    total_seconds = 0
    current_num = ''

    for char in duration_str:
        if char.isdigit():
            current_num += char
        elif char in ('s', 'm', 'h', 'd'):
            if not current_num:
                raise ValueError(f"Missing number before '{char}' in '{duration_str}'")
            value = int(current_num)
            if char == 's':
                total_seconds += value
            elif char == 'm':
                total_seconds += value * 60
            elif char == 'h':
                total_seconds += value * 3600
            elif char == 'd':
                total_seconds += value * 86400
            current_num = ''
        else:
            raise ValueError(f"Invalid character '{char}' in duration '{duration_str}'")

    if current_num:
        raise ValueError(f"Trailing number without unit in '{duration_str}'")

    if total_seconds == 0:
        raise ValueError(f"Empty or zero duration: '{duration_str}'")

    return timedelta(seconds=total_seconds)


def format_filesize(size_bytes: int, binary: bool = True) -> str:
    """Format a file size in bytes to a human-readable string.

    Args:
        size_bytes: Size in bytes (must be >= 0)
        binary: Use binary units (KiB, MiB) if True, decimal (KB, MB) if False
    """
    if size_bytes < 0:
        raise ValueError("Size cannot be negative")

    if binary:
        units = ['B', 'KiB', 'MiB', 'GiB', 'TiB']
        divisor = 1024
    else:
        units = ['B', 'KB', 'MB', 'GB', 'TB']
        divisor = 1000

    for unit in units[:-1]:
        if abs(size_bytes) < divisor:
            if unit == 'B':
                return f"{size_bytes} {unit}"
            return f"{size_bytes:.1f} {unit}"
        size_bytes /= divisor

    return f"{size_bytes:.1f} {units[-1]}"


def retry_with_backoff(func, max_retries: int = 3, base_delay: float = 1.0):
    """Execute a function with exponential backoff retry.

    Returns the function result on success, raises the last exception on failure.
    """
    import time

    last_exception = None
    for attempt in range(max_retries + 1):
        try:
            return func()
        except Exception as e:
            last_exception = e
            if attempt < max_retries:
                delay = base_delay * (2 ** attempt)
                time.sleep(delay)

    raise last_exception
```

## Acceptance Criteria

- [ ] Tests cover all three functions
- [ ] Happy path tests for normal inputs
- [ ] Edge case tests (zero, empty, boundary values)
- [ ] Error case tests (invalid inputs, expected exceptions)
- [ ] Tests are well-organized with descriptive names
- [ ] Tests actually run and pass

## Suggested Prompt

> "Write comprehensive tests for this utility module using pytest. Cover happy paths, edge cases, and error cases. Make sure the tests are well-organized and all pass."

## What to Observe

- How many test cases does it generate? Is the coverage thorough?
- Does it identify non-obvious edge cases (e.g., `parse_duration('0s')`, `format_filesize(0)`)?
- Does it use pytest features well (parametrize, fixtures, markers)?
- Does it test the `retry_with_backoff` function correctly (mocking `time.sleep`)?
- Does it create tests that actually run and pass, or do they have bugs?
- Does it suggest running the tests or just write them?
