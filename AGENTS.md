# AGENTS.md

## Cursor Cloud specific instructions

This is a pure Python scientific library (`atmosphericRadiationDoseAndFlux`) for calculating radiation dose rates in Earth's atmosphere. No external services, databases, or Docker containers are needed.

### Quick reference

| Action | Command |
|--------|---------|
| Install (editable) | `pip install -e .` |
| Install dev tools | `pip install flake8 pytest` |
| Lint (critical errors) | `flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics` |
| Lint (all warnings) | `flake8 . --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics` |
| Test | `pytest` |

### Known issues

- 2 of 8 tests (`test_comparison_to_original_DAF_proton_Flat`, `test_comparison_to_original_DAF_alpha_Flat`) fail with a `TypeError` on newer pandas (3.x) because `int()` is called on a `Series` instead of a scalar (missing `.iloc[0]`). This is a pre-existing test bug, not an environment issue.
- The `pkg_resources` deprecation warning from `particleResponse.py` is harmless.

### PATH note

`pip install --user` places scripts in `~/.local/bin`. If `flake8`/`pytest` are not found, ensure `~/.local/bin` is on `PATH`:
```
export PATH="$HOME/.local/bin:$PATH"
```
