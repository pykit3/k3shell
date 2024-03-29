# k3shell

[![Action-CI](https://github.com/pykit3/k3shell/actions/workflows/python-package.yml/badge.svg)](https://github.com/pykit3/k3shell/actions/workflows/python-package.yml)
[![Build Status](https://travis-ci.com/pykit3/k3shell.svg?branch=master)](https://travis-ci.com/pykit3/k3shell)
[![Documentation Status](https://readthedocs.org/projects/k3shell/badge/?version=stable)](https://k3shell.readthedocs.io/en/stable/?badge=stable)
[![Package](https://img.shields.io/pypi/pyversions/k3shell)](https://pypi.org/project/k3shell)

A python module to manage commands.

k3shell is a component of [pykit3] project: a python3 toolkit set.


#   Name

k3shell

#   Status

The library is considered production ready.




# Install

```
pip install k3shell
```

# Synopsis

```python

import k3shell
import sys
arguments = {
    'echo_repr': (
        lambda x: sys.stdout.write(repr(x)),
        ('x', {'nargs': '+', 'help': 'just an input message'}),
    ),

    'foo': {
        'bar': lambda: sys.stdout.write('bar'),

        'bob': {
            'plus': (
                lambda x, y: sys.stdout.write(str(x + y)),
                ('x', {'type': int, help: 'an int is needed'}),
                ('y', {'type': int, help: 'an int is needed'}),
            ),
        },
    },

    '__add_help__': {
        ('echo_repr',)           : 'output what is input.',
        ('foo', 'bar',)          : 'print a "bar".',
        ('foo', 'bob', 'plus',)  : 'do addition operation with 2 numbers.',
    },

    '__description__': 'this is an example command.',
}

k3shell.command(**arguments)
"""

then you can execute your command as:

python demo.py echo_repr hello!
# 'hello!'

python demo.py foo bar
# 'bar'

python demo.py foo bob plus 1 2
# 3


and you can get a usage help message like:

$ python demo.py -h
---------------------------
usage: demo.py [-h] {echo_repr, foo bar, foo bob plus} ...

this is an example command.

positional arguments:
  {echo_repr, foo bar, foo bob plus} commands to select ...
    echo_repr            output what is input.
    foo bar              print a "bar".
    foo bob plus         do addition operation with 2 numbers.

optional arguments:
    -h, --help           show this help message and exit


$ python demo.py foo bob plus -h
--------------------------
usage: demo.py foo bob plus [-h] x y

positional arguments:
    x   an int is need
    y   an int is need

optional arguments:
    -h, --help           show this help message and exit

"""
```

#   Author

Wenbo Li(李文博) <wenbo.li@baishancloud.com>

#   Copyright and License

The MIT License (MIT)

Copyright (c) 2017 Wenbo Li(李文博) <wenbo.li@baishancloud.com>


[pykit3]: https://github.com/pykit3