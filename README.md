# mini-dataframe

`mini-dataframe` is a lightweight, educational DataFrame-style library in pure Python.
It supports tabular data operations, basic statistics, filtering/querying, joins, concatenation, and simple CSV/JSON I/O.

## Features

- Core frame operations: `shape`, `head`, `tail`, `iloc`, `loc`, column selection, `drop`, `rename`, `sort_by`
- Statistics: `mean`, `sum`, `min`, `max`, `count`, `median`, `variance`, `std`, `mode`, `quantile`, `describe`
- Transformations: `group_by`, `filter_rows`, `map_column`, `drop_duplicates`
- Query DSL: expression-based filtering via `query(...)` and `select(..., where=...)`
- Relational operations: `join(...)` with `inner`, `left`, `right`, `outer`
- Concatenation: `MiniDataFrame.concat(..., axis=0|1)`
- File I/O: `from_csv`, `from_json`, `to_csv`, `to_json`

## Project structure

- `src/mini_dataframe/__init__.py`: public `MiniDataFrame` class
- `src/mini_dataframe/core.py`: core frame behavior, stats, transformations, I/O
- `src/mini_dataframe/merge.py`: joins and concat
- `src/mini_dataframe/dsl.py`: query expression compiler
- `tests/test_mini_dataframe.py`: pytest coverage for core behavior
- `test.py`: runnable demo script

## Requirements

- Python `3.8+`

## Setup

From the repository root:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -U pip
python -m pip install -e ".[dev]"
```

## Run the demo

```powershell
python test.py
```

## Run tests

```powershell
pytest -q
```

## Minimal usage example

```python
from mini_dataframe import MiniDataFrame

users = MiniDataFrame(
    {
        "user_id": [1, 2, 3],
        "name": ["Alice", "Bob", "Charlie"],
        "age": [25, 30, 35],
    }
)

print(users.shape())              # (3, 3)
print(users.query("age > 30"))    # rows where age > 30
print(users.describe())           # summary stats
```
