# Python Package Base Repository

A base repository for building Python projects, ready for being distributed as a python package, including testing support, code linter, styling utilites and GitHub Workflows.

## Instructions

Once you have copied the repo content, make sure to have a virtual environment (you can use Pip, Conda, etc...), install the requirements using:

```shell
pip install -r requirements-dev.txt
```

This will install:
- Pre-Commit: for using git hooks in order to maintain clean branches and commits
- Flake8: will be used for Python coding style
- Pytest: will be used for testing in Python, you can change it if you want
- Pytest-Cov: will be used for giving reports of the code coverage

After installing the requirements, and having initialized our git repository, we are going to set up pre-commit hook, just run:

```shell
pre-commit install
```

If we have not done any code change, we add the code to the git branch and test pre-commit:

```shell
git add .
pre-commit run
```

You should not have any errors if you have not touched the code, any code modification that Black or Isort does or any change that you have to do after running the command, means that you must add the modified code again to the commit, in order to let the hook check and validate the changes, you should have something like this in your terminal:

```shell
trim trailing whitespace.................................................Passed
fix end of files.........................................................Passed
check yaml...............................................................Passed
black....................................................................Passed
isort....................................................................Passed
flake8...................................................................Passed
```

Then we are going to run the tests, this one is a simple test that asserts true, so it should not give any error:

```shell
pytest --cov-report term --cov ./
```

Once everything is OK, I suggest to do a first commit in order to test the CI workflow and push it to your repo, notice that if you want to use Bitbucket CI, Gitlab CI or another CI, you should make the proper configuration file, this repo only covers GitHub CI.
