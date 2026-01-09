# Test Case: Mixed Pip + Poetry Project

## Package Manager
Mixed (both pip and poetry files present)

## Python Version Detection
- **Source**: pyproject.toml
- **Expected**: Tool should detect this as Poetry (due to poetry.lock) and use tool.poetry.dependencies.python = "^3.10"
- **Conflict**: requirements.txt also present (typical in transitioning projects)

## Files Present
- requirements.txt (pip manifest)
- pyproject.toml (poetry manifest with both tool.poetry and project sections)
- poetry.lock (indicates Poetry is the package manager)

## Test Purpose
Real-world scenario: Projects transitioning from pip to Poetry, or maintaining both.
Tool must:
1. Identify correct package manager (Poetry due to poetry.lock)
2. Use Poetry priority order (tool.poetry.dependencies.python first)
3. Ignore pip-specific files for versioning

## Expected Behavior
- Package manager detection: Poetry (not pip)
- Version source: tool.poetry.dependencies.python = "^3.10"
- requirements.txt should be IGNORED for version detection
