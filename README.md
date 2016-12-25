# PyConfImporter

A utility to define an external Python config module for your Python project.

For example, in your project, you may have a module called `settings.py` with
the following:

    DB_HOST = '...'
    DB_USER = '...'
    DB_PASS = '...'

You don't want to commit these values to your repository, so instead you define
`settings.py` as follows:

    from pyconfimporter import Required, inject

    DB_HOST = 'localhost'  # Example of default value
    DB_USER = Required
    DB_PASS = Required

    inject('path/to/external_config.py')

Now `settings.py` is clear of credentials. `external_config.py` can be located
anywhere in your filesystem (e.g. `/etc/project/external_config.py`) and should
have the exact contents as the originally defined `settings.py` file.

# Why?

I've found this useful when your settings are not simple constants, but instead
complex Python structures. Use this if defining these structures is cumbersome
to define in another config format such as JSON, XML, or
[Python's configparser](https://docs.python.org/3/library/configparser.html).

# Install

    pip install pyconfimporter

