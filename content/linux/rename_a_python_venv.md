Title: How to rename (and backup) a Python virtual environment
Date: 2022-05-16
Modified: 2022-05-25 07:20
Category: Linux
Tags: python, venv, pip, backup
Slug: rename-a-python-venv
Author: Tamas Molnar

**Video:** [YouTube video presentation of the post](https://youtu.be/sesa3ngoU74)

**In short:** I find it much easier to create a venv with the same packages than renaming one.
I found magic `sed` commands and directory traversal scripts, but they did a half work or nothing.
I found out that recreating an env is easier and faster.

Activate the old venv and query the packages with [pip freeze](https://pip.pypa.io/en/stable/cli/pip_freeze/):
```
pip freeze > requirements.txt
```

The command will write a `requirements.txt` file with the currently installed packages and versions.

**Save this file for later use!**

Create a new venv with the desired name:
```
python3 -m venv test_venv
```

Activate the new environment:
```
source test_venv/bin/activate
```

Now we can [install](https://pip.pypa.io/en/stable/cli/pip_install/) the packages from our old environment with using the `requirements.txt` file:
```
pip install -r requirements.txt
```

Now the old env can be deleted or moved away.

1. [Python PIP documentation](https://pip.pypa.io/en/stable/user_guide/)
1. [Python venv documentation](https://docs.python.org/3/library/venv.html)