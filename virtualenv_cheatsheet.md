# Ben's VirtualEnv Cheatsheet #

This cheat sheet describes my usage/implementation of virtualenv with virtualenv wrapper and the bash foo that I added with the help of many blogs to make it all tick together in fun land. 

**Quick Reference**

    $ echo $WORKON_HOME
    /Users/benjamin/.virtualenvs

    $ echo $PROJECT_HOME
    /Users/benjamin/Repos/git/

## Commands ##

All of the commands below are to be used on the Terminal Command line.

#### venv ####
List or change working virutal environments (alias `workon`)

    venv [environment_name]

#### venv.exit ####
Switch from the virtual environment back to system Python (alias `deactivate`)
    
    venv.exit
    
#### venv.ls ####
List all of the environments (alias `lsvirtualenv`)

    venv.ls [-b] [-l] [-h]

`-b` Brief mode, disables verbose output
`-l` Long mode, verbose output, default
`-h` Print help

#### venv.show ####
Show the details for a single virtualenv
    
    venv.show [env]

#### venv.init ####
Create a new environment in the `WORKON_HOME` (alias `mkvirtualenv`)

    venv.init ENVNAME
    venv.init [-a project_path] [-i package] [-r requirements.txt] [virtualenv opts] ENVNAME

#### venv.rm ####
Remove an environment in the `WORKON_HOME` (alias `rmvirtualenv`). Note that you must be deactivated before you can remove the current environment.
    
    venv.rm ENVNAME

#### venv.switch ####
A semantic alias for `venv` (e.g. `workon`) to faciliate switching to other virtual environments.
    
    venv.switch ENVNAME

#### venv.add ####
Adds the specified directories to the Python path for the currently active virutal environment (alias `add2virtualenv`). Useful for providing non-pip packages or local development packages into the enivronment without messing with .pth files.
    
    venv.add dirpath dirpath ..

#### venv.cd ####
Changes the current working directory to the one specified as the project directory for the active virtual env (alias `cdproject`). Note that you must have the project specified.
    
    venv.cd

#### venv.cdsp ####
Changes the current working directory to the `site-packages` directory of the current virtual environment (alias `cdsitepackages`).
    
    venv.cdsp [subpackage]

#### venv.cdenv ####
Changes the current working directory to the directory of the current virtual environmment (alias `cdvirtualenv`).
    
    venv.cdenv [subdir]

#### venv.lssp ####
Lists the contents of the site-packages directory in the current active virtual environment (alias `lssitepackages`).

    venv.lssp

#### venv.proj ####
Create a new virtualenv and a new project directory in associated HOME directories (alias `mkproject`).
    
    venv.proj [-f|--force] [-t template] [virtualenv opts] ENVNAME

#### venv.setproj ####
Bind an existing virtualenv to an existing project (alias `setvirtualenvproject`)

    venv.setproj [virtualenv_path project_path]

An association is made so thtat when venv activtes the virtualenv the project is also activated. 

Note that if no arguments are provided, the current virtualenv and the current working directory are assumed.

#### venv.wipe ####
Remove all of the installed third-party packages in the current virtualenv (alias `wipeenv`).
    
    venv.wipe

### Dependencies ###

In order to make this happen you need to install the following:
    
* pip
* virtualenv
* virtualenvwrapper

## Appendix: .bash_profile ##
 
    # virtualenv
    export WORKON_HOME=$HOME/.virtualenvs
    export PROJECT_HOME=$HOME/Repos/git/
    source /usr/local/bin/virtualenvwrapper.sh
    
    alias venv="workon"
    alias venv.exit="deactivate"
    alias venv.ls="lsvirtualenv"
    alias venv.show="showvirtualenv"
    alias venv.init="mkvirtualenv"
    alias venv.rm="rmvirtualenv"
    alias venv.switch="workon"
    alias venv.add="add2virtualenv"
    alias venv.cd="cdproject"
    alias venv.cdsp="cdsitepackages"
    alias venv.cdenv="cdvirtualenv"
    alias venv.lssp="lssitepackages"
    alias venv.proj="mkproject"
    alias venv.setproj="setvirtualenvproject"
    alias venv.wipe="wipeenv"