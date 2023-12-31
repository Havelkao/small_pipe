# small_pipe

small_pipe (small_pp for short) is a minimal abstraction layer for piping operations in python.

## Install
```shell
pip install small_pipe
```

## Examples

You can alias your functions and then use it in the pipe function like so

```python
import small_pipe as pp

exists = pp.where(lambda x: x is not None)

pp.pipe(
    [1, 2, 3, None, 4],
    exists
)
```

```python
[1, 2, 3, 4] # returns
```

For more complex cases consider importing functions directly as in

```python
from small_pipe import pipe, each, where, reduce

pipe.debug = True
double = lambda x: x * 2

pipe(
    range(15),
    each(double),
    where(lambda x: x % 2 == 0),
    list,
    reduce(lambda x, y: x + y, 20),
    double
)
```

```python
<map object at 0x000002055852B1F0>
<filter object at 0x000002055852B040>
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28]
230
460  # returns
```

## Docs

`pipe` is literally just a function that loops over \*args and calls them on the positional argument

`each`, `where` and `reduce` wrap higher order functions `map`, `filter` and `functools.reduce` respectively so that they can be used without the iterable argument
