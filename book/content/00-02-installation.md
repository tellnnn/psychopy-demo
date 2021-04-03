---
title: Installation
author: Teruaki Kido
---

# Installation

As a first step, it is nice to read through [Installation](https://www.psychopy.org/download.html) to understand available methods to install PsychoPy.

In this section, I will introduce how to install PsychoPy using `pipenv`, as an alternative way.

> Pipenv is a tool that aims to bring the best of all packaging worlds (bundler, composer, npm, cargo, yarn, etc.) to the Python world. Windows is a first-class citizen, in our world.
> 
> It automatically creates and manages a virtualenv for your projects, as well as adds/removes packages from your Pipfile as you install/uninstall packages. It also generates the ever-important Pipfile.lock, which is used to produce deterministic builds.
>
> (ref: https://github.com/pypa/pipenv (2021/04/03))

```{warning}
The following codes are assumed to be run under macOS, but you can find appropriate codes for your systems from the embedded links.
```


## Install `pyenv`

Here, to install Python with a specific version, I will use `pyenv`. Importantly, it is recommended to use Python 3.6 for now (2021-04-03).

To install `pyenv`, please follow [Installation](https://github.com/pyenv/pyenv#installation) document. As an example, people who use macOS may install `Homebrew` and run:

```
brew update
brew install pyenv
```

Then, add `pyenv init` to your shell (zsh as an example):

```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
source ~/.zshrc
```

Finally, check the version of installed `pyenv`:

```
pyenv --version
```


## Install Python 3.6

With `pyenv` you can check available Python versions:

```
pyenv install --list
```

You will find the latest version of Python 3.6 (`3.6.13` on 2021-04-03). Then, install that version of Python with:

```
pyenv install 3.6.13
pyenv global 3.6.13
```

```{note}
Here, I put the line `pyenv global 3.6.13` to set the global Python version, for simplicity. Similarly, you can change the global Python version with `pyenv global X.X.X`.
```

The following line should return `Python 3.6.13`:

```
python --version
```


## Install `pipenv`

Upgrade `pip` and install `pipenv` with:

```
python -m pip install --upgrade pip
python -m pip install pipenv
```

```{note}
The above lines follow [Pragmatic Installation of Pipenv](https://pipenv.pypa.io/en/latest/install/#pragmatic-installation-of-pipenv) under [Installing Pipenv](https://pipenv.pypa.io/en/latest/install/#installing-pipenv). Of course, you can choose another method instead.
```

:::{note}
If you received the warning saying:

```
WARNING: The scripts pipenv and pipenv-resolver are installed in '/Users/yourname/.local/bin' which is not on PATH.
Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
```

run the following lines additionally:

```
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```
:::

Finally, check the version of installed `pipenv`:

```
pipenv --version
```


## Create Project Directory

When it comes to use PsychoPy in a project, it will be appropriate to make a project directory. For now, I will make a directory named `psychopy-demo-book`:

```
mkdir psychopy-demo-book
cd psychopy-demo-book
```


## Install PsychoPy

Finally, you can install PsychoPy with:

```
pipenv --python 3.6
pipenv install psychopy
pipenv shell
```

The first line creates a virtual environment with Python 3.6, the second line install the latest version of PsychoPy with its dependencies under the virtual environment, and the third line launches the virtual environment.
