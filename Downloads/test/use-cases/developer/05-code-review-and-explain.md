# Use Case: Code Review and Explain

## Objective

Ask the AI tool to review and explain an unfamiliar codebase. Tests the tool's ability to comprehend code, identify issues, and communicate clearly about complex logic.

## The Task

Give the tool access to an open-source project you're not deeply familiar with (or use the example below) and ask it to:

1. **Explain** what the code does at a high level
2. **Review** it for bugs, security issues, and code quality problems
3. **Suggest** specific improvements with rationale

### Example Code to Review

```python
import hashlib
import os
import json
from functools import wraps
from time import time

class RateLimiter:
    def __init__(self, max_requests, window_seconds):
        self._store = {}
        self.max_requests = max_requests
        self.window = window_seconds

    def _cleanup(self, key):
        now = time()
        if key in self._store:
            self._store[key] = [t for t in self._store[key] if now - t < self.window]

    def is_allowed(self, key):
        self._cleanup(key)
        if key not in self._store:
            self._store[key] = []
        if len(self._store[key]) >= self.max_requests:
            return False
        self._store[key].append(time())
        return True

    def __call__(self, func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            key = f"{func.__name__}:{args}:{kwargs}"
            if not self.is_allowed(key):
                raise Exception("Rate limit exceeded")
            return func(*args, **kwargs)
        return wrapper


class SimpleCache:
    def __init__(self, maxsize=128, ttl=300):
        self.maxsize = maxsize
        self.ttl = ttl
        self.cache = {}
        self.access_order = []

    def _make_key(self, args, kwargs):
        return hashlib.md5(json.dumps((args, sorted(kwargs.items())), default=str).encode()).hexdigest()

    def get(self, key):
        if key in self.cache:
            entry = self.cache[key]
            if time() - entry['time'] > self.ttl:
                del self.cache[key]
                self.access_order.remove(key)
                return None
            self.access_order.remove(key)
            self.access_order.append(key)
            return entry['value']
        return None

    def set(self, key, value):
        if key in self.cache:
            self.access_order.remove(key)
        elif len(self.cache) >= self.maxsize:
            oldest = self.access_order.pop(0)
            del self.cache[oldest]
        self.cache[key] = {'value': value, 'time': time()}
        self.access_order.append(key)

    def __call__(self, func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            key = self._make_key(args, kwargs)
            result = self.get(key)
            if result is not None:
                return result
            result = func(*args, **kwargs)
            self.set(key, result)
            return result
        return wrapper


def generate_token(length=32):
    return hashlib.sha256(os.urandom(length)).hexdigest()
```

## Acceptance Criteria

- [ ] Provides a clear, accurate high-level explanation
- [ ] Identifies at least 3 real issues (there are several: thread safety, memory leak in RateLimiter, cache can't store None/falsy values, md5 for cache keys, generic Exception)
- [ ] Suggestions are specific and actionable (not vague "consider improving")
- [ ] Explains the why, not just the what
- [ ] Doesn't flag non-issues as problems (no false positives)

## Suggested Prompt

> "Review this code. First explain what it does at a high level, then identify any bugs, security issues, or quality problems. Suggest specific improvements."

## What to Observe

- Does it understand the decorator pattern and LRU-like cache behavior?
- Does it spot the subtle bugs (cache returning None for falsy cached values, unbounded growth in RateLimiter)?
- Does it flag security issues (md5 usage, generic exceptions)?
- Are its suggestions practical or overly theoretical?
- Does it distinguish between critical issues and nice-to-haves?
- How well does it explain complex concepts (closures, decorators, hashing)?
