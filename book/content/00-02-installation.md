# Installation

As the first step, it is nice to read through [PsychoPy installation instructions](https://www.psychopy.org/download.html) to understand available ways to install PsychoPy.

```{warning}
In this section, I will introduce how to install PsychoPy using `pipenv`, as **an alternative way**. Therefore, you don't have to follow the following steps to install PsychoPy. The ways in the above link may be easier than the below.
```

```{warning}
The codes in this section are assumed macOS and zsh, but you can find appropriate codes for your systems from the embedded links within the text.
```


## Install `pyenv`

For reproducibility, it will be appropriate to specify the Python version in your project. To accomplish this, we will use `pyenv` below.

> pyenv lets you easily switch between multiple versions of Python. It's simple, unobtrusive, and follows the UNIX tradition of single-purpose tools that do one thing well.[^pyenv]

[^pyenv]: https://github.com/pyenv/pyenv (accessed: 2021-04-04)

To install `pyenv`, please follow [`pyenv` installation instructions](https://github.com/pyenv/pyenv#installation). 

For example, people who use macOS (and zsh) may install `Homebrew`, the Python build dependencies with `Homebrew`, and install `pyenv` with:

```bash
brew update
brew install pyenv
```

Then, add several lines to your shell with:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
source ~/.zshrc
```

Finally, check the version of installed `pyenv` with:

```bash
pyenv --version
```


## Install Python

Here we will use Python 3.8, for example. You can check available Python versions with `pyenv`:

```bash
pyenv install --list
```

You will find the latest version of Python 3.8 (`3.8.8` on 2021-04-02). Then, install that version of Python with:

```bash
pyenv install 3.8.8
pyenv global 3.8.8
```

```{note}
Here, I set the global Python version with `pyenv global 3.8.8`, just for simplicity. After installation, you can change it with `pyenv global X.X.X`.
```

The following line should return `Python 3.6.13`:

```bash
python --version
```


## Install `pipenv`

For reproducibility, it will be appropriate to specify the package versions in your project. To accomplish this, we will use `pipenv` below.

> Pipenv is a tool that aims to bring the best of all packaging worlds (bundler, composer, npm, cargo, yarn, etc.) to the Python world. *Windows is a first-class citizen, in our world.*
> 
> It automatically creates and manages a virtualenv for your projects, as well as adds/removes packages from your `Pipfile` as you install/uninstall packages. It also generates the ever-important `Pipfile.lock`, which is used to produce deterministic builds.[^pipenv]

[^pipenv]: https://github.com/pypa/pipenv (accessed: 2021-04-04)

With Python of the specified version, upgrade `pip` and install `pipenv` with:

```bash
python -m pip install --upgrade pip
python -m pip install --user pipenv
```

```{note}
The above lines follow the section "[Pragmatic Installation of Pipenv](https://pipenv.pypa.io/en/latest/install/#pragmatic-installation-of-pipenv)" under `pipenv` installation instructions. Of course, you can choose another method instead.
```

:::{note}
If you received the warning saying:

> `WARNING: The scripts pipenv and pipenv-resolver are installed in '/Users/yourname/.local/bin' which is not on PATH.`
> 
> `Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.`

Then, run the following lines additionally:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```
:::

Finally, check the version of installed `pipenv`:

```bash
pipenv --version
```


## Create Project Directory

When it comes to use PsychoPy in a project, it will be appropriate to make a project directory. For now, I will make a directory named `psychopy-demo-book`:

```bash
mkdir psychopy-demo-book
cd psychopy-demo-book
```


## Install PsychoPy

Finally, you can install PsychoPy with:

```bash
pipenv --python 3.8
pipenv install psychopy
pipenv shell
```

The meaning of each line is:

1. creates a virtual environment with Python 3.8
2. installs the latest version of PsychoPy with its dependencies under the virtual environment
3. launches the virtual environment.
