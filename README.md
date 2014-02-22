# virtualenv cheatsheet #
**Helpers for virtualenv and virtualenvwrapper.**

## Setup ##

1. Install virtualenv and virtualenvwrapper with pip or your preferred method. 
2. Copy the enviornment variables from `bash_environ` to your `.profile` or `.bashrc` or `.bash_profile`
3. Source your profile (or exit and reopen your terminal)

## Read ##

Check out the [cheatsheet](virtualenv_cheatsheet.md) for recommendations on how to use these helpers.

## Python Package setup ##

This is my normal method to setup a Python project:

1. Create a directy in `$PROJECT_HOME` for my project lets name it "project"
2. `cd $PROJECT_HOME/project
3. git init
4. touch .gitignore
5. venv.init -a $(pwd) project
6. mkdirs docs tests project bin
7. touch tests/__init__.py
8. touch project/__init__.py
9. touch setup.py
10. pip install (whatever you need)
11. pip freeze > requirements.txt
12. touch README.md
13. touch LICENSE

At this point you should have everything you need to get started (commit your initial structure and go!)
