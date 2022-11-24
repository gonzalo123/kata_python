## Python dummy project for TDD 
http://katayunos.com/

## Activate virtualenv
```shell
python -m venv venv
source venv/bin/activate
pip install --upgrade pip 
pip install -r requirements.txt
```

## run tests
> pytest

or

> python -m pytest tests/

## pyenv tips
### Simple test
tests/test_app.py
```python
from app import foo

def test_foo():
    assert foo() is False, "first test must fail"
```

app.py
```python
def foo():
    return False
```

### Fixtures

tests/conftest.py
```python
import pytest


@pytest.fixture()
def demo_fixture():
    return 1
```

Using fixture in test

tests/test_app.py
```python
def test_fixture(demo_fixture):
    assert 1 == demo_fixture, "fixture demo"
```

### Using parametrized tests

tests/test_app.py
```python
import pytest

testdata = [
    ("0", 0),
    ("1", 1),
    ("2", 2),
]
@pytest.mark.parametrize("actual, expected", testdata)
def test_parametrize(actual, expected):
    assert int(actual) == expected
```

### pytest doc
https://realpython.com/pytest-python-testing/
https://docs.pytest.org/en/7.2.x/