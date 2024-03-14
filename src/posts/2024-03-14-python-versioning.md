---
title: 'Python Versioning'
date: '2024-03-11'
tags:
  - python
  - versions
  - devops
---

"It's versions all the way down" - ChatGPT

![Python, packages and code stacked on top of each other](/images/2024-03-13-python-versioning/versions.png)

Much of managing code and dependencies comes down to version management. This post focuses on Python versioning but
the concepts can be applied to other languages and tools.

### Python Versioning

[Python](https://www.python.org/downloads/) comes in different versions. 3.13 is in a prerelease state. 3.12 is the latest stable version. You should try to use the latest stable version for your projects but some dependencies may not be compatible with the latest version.

![Python versions](/images/2024-03-13-python-versioning/python_versions.png)

Here I'm using Python 3.11.6.

```
$ python3 --version
Python 3.11.6
```

It's helpful to have a version manager for Python in case you're developing on multiple projects with different Python versions. [pyenv](https://github.com/pyenv/pyenv) is a popular version manager for Python. It allows you to install and switch between different Python versions.

If it's your first time managing language versions, it can get complicated if you run into pathing issues. If you can avoid using multiple versions, it might be easier just to use a single version of Python installed from the official website.

### Package Management

Python's package ecosystem is pretty complicated. There are different tools and they do similar things so it can be confusing and hard to know which one to use. Here are a few to know.

* pip
* anaconda
* poetry
* pipenv
* virtualenv

#### What does ChatGPT say?

You

which should i use?

* pip
* anaconda
* poetry
* pipenv
* virtualenv


ChatGPT

The choice between these tools depends on your specific needs and preferences. Here's a brief overview of each:

pip: This is the default package manager for Python. It's simple and widely used for installing Python packages from the Python Package Index (PyPI). It's a good choice if you want simplicity and don't need additional features like environment management.

Anaconda: Anaconda is a distribution of Python that comes with its own package manager called conda. It's popular in the data science community because it includes a wide range of pre-installed libraries commonly used in data analysis and machine learning. If you're working with data science tools or need a pre-configured environment, Anaconda can be a good choice.

Poetry: Poetry is a tool for managing Python dependencies and packaging. It's particularly useful for managing project dependencies and handling virtual environments. If you're working on a Python project and want a modern, dependency management-focused tool, Poetry could be a good fit.

pipenv: Pipenv is a dependency management tool for Python that aims to bring the best of all packaging worlds (bundled dependencies, development requirements, etc.) to the Python world. It automatically creates and manages a virtual environment for your projects, as well as adds/removes packages from your Pipfile as you install/uninstall packages. If you want something that combines package management with virtual environment management, pipenv might be a good choice.

virtualenv: Virtualenv is a tool to create isolated Python environments. It allows you to create separate environments for each of your projects, which helps keep dependencies separate and avoids conflicts between different projects. Virtualenv is often used in combination with pip for package management. If you need lightweight virtual environment management, virtualenv is a good choice.

Ultimately, the best tool for you depends on your specific requirements, the nature of your project, and your personal preferences. If you're not sure, you might want to experiment with a few of them to see which one you're most comfortable with.

#### In simplier terms

pip is our package manager. It's the default and widely used. It's simple and good if you don't need additional features like environment management.

Anaconda and virtualenv are for managing environments. Say you have multiple projects and they require different versions of the same package. You can use these tools to isolate the packages for each project away from each other.

Poetry and pipenv are for managing project as a whole. They combine the two ideas of package management and environment management. They automatically create and manage virtual environments for your projects.

### Examples

I created a simple example with pip and dotenv.

dotenv is a common way to manage environments in not just Python but other languages as well. It's a way to store environment variables in a file and load them into your environment. By keeping them all in one file, it's easier to manage and avoid leaking secrets by accidentally pushing to a public repository.

[https://github.com/lamroger/python-env-examples](https://github.com/lamroger/python-env-examples)

### Conclusion

As you work with more projects or with more collaborators, you may need to start using anaconda or poetry or other tooling. Keep it simple and only use what you need. It's better to get comfortable with one tool and then expand to others as you need them.
