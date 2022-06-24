Create the actual package

```sh
poetry new dummy_pkg
```

Assign it to git


Create the **test_poetry** environment which will host the jupyter notebook and the package to be developed as editable
```sh
poetry new test_poetry
cd test_poetry

poetry add ipykernel
poetry run python -m ipykernel install --name=dummy_dvl_env

poetry add [SOME_PATH]/dummy_pkg
```

Set the dummy_pkg as editable in `test_poetry/pyproject.toml`

```python
dummy-pkg = {path = "../dummy_pkg",  develop = true}
```

Remove any previous trace of the dummy_pkg initaly installed

Guess the location of the depedency folder
```sh
poetry shell
python
```
```python
import dummy_pkg
dummy_pkg.__file__
```
Remove the package and the dist-info folders
```sh
rm -rf [SOME_PATH]/pypoetry/virtualenvs/test-poetry-[SOME_HASH]-py3.X/lib/python3.X/site-packages/dummy_pkg*
```
Remove the poetry-lock

```sh
rm poetry.lock
```

Reinstall the package
``sh
poetry install
``

Check the presence of symbolic link in the dependencies folder aka `/site-packages/dummy_pkg.pth`
