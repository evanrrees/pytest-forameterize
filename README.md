# Parameterize, with an 'e'
'Cleaner' is subjective. The `pytest.mark.parametrize` decorator can sometimes be difficult to read when there are many 
arguments, or argument values are nested. This package provides the `make_args` factory function for generating typed 
arguments to parametrize a test function using the `pytest_parametrize.parametrize` decorator.

## Installation

```bash
pip install pytest_parametrize
```

## Usage

```python
import forameterize

AddArgs=forameterize.make_args(
    "AddArgs",
    a=int,
    b=int,
    result=int,
)


@forameterize.forameterize(
    AddArgs("both positive", a=1, b=2, result=3),
    AddArgs("both negative", a=-1, b=-2, result=-3),
    AddArgs("mixed", a=-1, b=2, result=1),
    AddArgs("both zero", a=0, b=0, result=0),
)
def test_adding(a, b, result):
    assert a + b == result
```

Equivalent with vanilla pytest:

```python
import pytest


@pytest.mark.parametrize(
    argnames=["a", "b", "result"],
    argvalues=[
        (1,  2,  3),
        (1, -2, -3),
        (1,  2,  1),
        (0,  0,  0)
    ],
    ids=[
        "both positive",
        "both negative",
        "mixed",
        "both zero",
    ]
)
def test_adding(a, b, result):
    assert a + b == result
```

# Open questions
What should this stupid thing be called?

- parameterize
- pyrametrize
- pyrametryze
- pyrymytyryze
- pyrymytryze
- forameterize
- forameteryze