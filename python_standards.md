# Python coding standards document


## Provisioning your machine

In terms of setting up your local development environment, choose any Linux distro that you feel comfortable with. To provision the environment, you'll need to install the following system dependencies: 

1. Python 3.4 or higher.
2. python3-dev.
3. virtualenv.
4. python3-pip.
5. Git.
6. freetds-dev.
7. Docker.
8. Docker compose.

In a Debian-based distribution, you can install these dependencies with the following command:

```
$ sudo apt-get update
$ sudo apt-get -y install python3 python3-dev virtualenv python3-pip git freeteds-dev docker 
$ pip3 install docker-engine
```

-----------------------

## Provision a virtual environment

When working on a Python project, you need to set up a virtual environment that allows you managing the dependencies of your application. To set up a virtual environment, folow the following steps:

```
$ git clone <a_project>
$ cd <project_directory>
$ virtualenv venv --python=python3
$ source venv/bin/activate
(venv)$ pip install -r requirements.txt
(venv)$ python setup.py install
```

### Managing your projec'ts dependencies:

Make sure you create and activate a virtual environment at the start of any project. As you start installing dependencies, freeze them in a `requirements.txt` file with the following command:

`$ pip freeze > requirements.txt` 

-----------------------

## Naming conventions

-----------------------

## Documenting your code

Python uses docstrings to generate documentation from the source code. The standards on how to write docstrings are described in PEP257 (https://www.python.org/dev/peps/pep-0257/). 

When it comes to a specific format to write docstrings, there are in Python three main options:

1. Google syle. Example: http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html.

2. Sphinx style, which uses resTructuredText, a kind of markdown. Example: http://documentation-style-guide-sphinx.readthedocs.io/en/latest/style-guide.html. 

3. NumPy style. Example: http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_numpy.html#example-numpy. 

We'll use the Google style becuase of its clarity, and also because it has proven compatibility with doxygen when using doxypypy (https://pypi.python.org/pypi/doxypypy/).

### When documenting your code, the following standards apply:

1. All docstrings are wrapped by three starting and three closing double quotation marks: `"""Docstrings"""`.

2. Start every file with a module level description. This description should include the following elements:

	2.1. A one-line description of the module.
	2.2. A summary of the module's purpose and intent.
	2.3. A list of all relevant elements within the module which are relevant for consumers of the module's API. This includes variables, functions, and classes, together with a one line description of each. 

3. At the package level, document the package in __init__.py. Again, list those elements from within the package, including subpackages, which are relevant for its consumers, and provide brief descriptions. 





-----------------------

## `import` statements

Import statements must be grouped on top of a file according to the following rules:

1. First come imports from the Python core library.

2. Following a blank line, include import statements from third party libraries.

3. Following a blank line, include import statements from your own project. 

-----------------------

## Structure of a python file

1. Start all of your files with a shebang line like this:

```
#!/usr/bin/env python3
```

2. Following the shebang line, include module level docstrings.

3. After the docstrings, include `import` statements. 

4. Declare any module level variables. DON'T use `globals()`. 

5. Implement module level functions.

6. Implement module level classes.

7. If warranted (but not usually recommended since it's rather a sign of code smell), include the following line at the end of the file:

```python
if __main__ == '__main__':
	do_some_code()
```

-----------------------

## Structuring code within a package:

The root of a package will typically include the following elements:
```
.
+-- .gitignore
+-- application_code/
|   +-- __init__.py
+-- application_entry_point.py
+-- Optional: config/
+-- docker/
|   +-- Dockerfile
|   +-- Dockerfile.test
|   +-- test.sh
+-- Optional: examples/
+-- Optional: Makefile / Fabfile
+-- README.md
+-- requirements.txt
+-- setup.py
+-- tests/
|   +-- __init__.py

```

The above tree represents a library structure. application_code/ is the package containing the code. In Python, you typically name this directory with the name of the library, and it represents the point of entry to your library code. Other alternatives less frequently used in the Python community are src/ and lib/. 

### When designing and working on a package, the following rules apply:

1. Every package must contain `__init__.py` file.

2. Group custom exceptions in an exceptions.py module, or in several modules within an exceptions subpackage.

3. 

-----------------------

## Testing 

-----------------------

## `setup.py` file


-----------------------


## `__init__.py` file


-----------------------

## Data structures


-----------------------


## Classes and inheritance 

