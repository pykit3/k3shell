# k3shell

[![Action-CI](https://github.com/pykit3/k3shell/actions/workflows/python-package.yml/badge.svg)](https://github.com/pykit3/k3shell/actions/workflows/python-package.yml)
[![Documentation Status](https://readthedocs.org/projects/k3shell/badge/?version=stable)](https://k3shell.readthedocs.io/en/stable/?badge=stable)
[![Package](https://img.shields.io/pypi/pyversions/k3shell)](https://pypi.org/project/k3shell)

Shell command dispatcher with nested subcommand support.

k3shell is a component of [pykit3](https://github.com/pykit3) project: a python3 toolkit set.

## Installation

```bash
pip install k3shell
```

## Quick Start

```python
import k3shell
import sys

# Define command structure with nested subcommands
arguments = {
    'echo': (
        lambda x: sys.stdout.write(repr(x)),
        ('x', {'nargs': '+', 'help': 'input message'}),
    ),
    'math': {
        'add': (
            lambda x, y: print(x + y),
            ('x', {'type': int}),
            ('y', {'type': int}),
        ),
    },
}

# Run command dispatcher
k3shell.command(**arguments)
```

Usage:
```bash
python my_cli.py echo hello world
python my_cli.py math add 1 2
```

## API Reference

::: k3shell

## License

The MIT License (MIT) - Copyright (c) 2015 Zhang Yanpo (张炎泼)
