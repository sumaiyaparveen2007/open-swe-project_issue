# open-swe-project_issue

Simple user tracker for storing users, validating ages, and calculating age-based summaries.

## Features

- Add users with validated positive integer ages
- Prevent duplicate user names
- Calculate the average age safely when no users exist
- Find the oldest user correctly

## Usage

The source file in this repository is named `issue` without a `.py` suffix, so it is loaded directly from disk.

```python
import importlib.util
from importlib.machinery import SourceFileLoader
from pathlib import Path

loader = SourceFileLoader("issue", str(Path("issue")))
spec = importlib.util.spec_from_loader(loader.name, loader)
issue = importlib.util.module_from_spec(spec)
loader.exec_module(issue)

issue.add_user("Amina", 21)
issue.add_user("Noah", 34)

print(issue.average_age())
print(issue.oldest_user())
```

## Run tests

```bash
python -m unittest test_issue.py
```

## Notes

- `average_age()` returns `0.0` when there are no users.
- `oldest_user()` returns `None` when there are no users.
