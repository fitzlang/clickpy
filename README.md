# clickpy

Automated mouse clicker script.

## Installation

I've only tested this packag with Python 3.9. You'll need to download and install it, or use [pyenv][2] and set your local version with this command:

```bash
pyenv local 3.9
```

I also recommend using [pipx][7] for installing standalone packages, as it will add a layer of isolation to your installation. But pip will work too:

```bash
pipx install clickpy
# -- or --
pip install clickpy
```

## Development

Using [Poetry][1] to manage the virtual environment and packages. I also highly recommend using [Pyenv][2] to install and manage your python interpreters.

This script uses [pyautogui][3] for clicking and [Typer][4] for CLI parsing.

### Testing

This project utilizes [pytest][5] and [pytest-mock][6]. Both should be included in pyproject.toml dev dependencies, and `.vscode/settings.json` should already be setup to use these libraries.

Please type annotate any mocks used, which should be `MockerFixture` if you use pytest-mock.

### Scripts

The following is for developers. You don't need to run these scripts to install and run from pip.

```bash
# define your local python version
pyenv local 3.9.6
```

```bash
# install all deps from pyproject.toml
poetry install
```

To run clickpy with poetry. This will activate the virtualenv, and then run the script defined in `[tool.poetry.scripts]` in pyproject.toml.

```bash
poetry run clickpy
```

TODO: might look into tox later, also pre-commit looks interesting.

```bash
# activate virtual environment first
poetry shell
# run tests, also outputs code coverage
pytest -v --cov=clickpy tests/

# -- or --

# run this outside virtualenv
poetry run pytest -v --cov=clickpy tests/
```

```bash
# run tox tests
poetry env tox

# -- or --
poetry shel
tox

# you may need to run this command, if pyautogui throws errors
touch ~/.Xauthority
```

```bash
# run this to generate report
coverage html
# open html coverage
open htmlcov/index.html

# -- or --

# for windows, opening html coverage
start htmlcov/index.html
```

Open coverage report in bash. This should also work with Windows Git Bash

```bash
# open html coverage doc, windows doesn't have open.
[ -x "$(command -v open)" ] && open htmlcov/index.html || start htmlcov/index.html
```

```sh
# same command for fish shell
[ -x (command -v open) ] && open htmlcov/index.html || start htmlcov/index.html
```

[1]: https://github.com/python-poetry/poetry
[2]: https://github.com/pyenv/pyenv
[3]: https://github.com/asweigart/pyautogui
[4]: https://github.com/tiangolo/typer
[5]: https://github.com/pytest-dev/pytest
[6]: https://github.com/pytest-dev/pytest-mock
[7]: https://github.com/pypa/pipx
