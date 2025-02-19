.. include:: targets.rst

Plugins
=======

Nitpick uses plugins to handle configuration files.

There are plans to add plugins that handle certain file types, specific files, and user plugins.
Check `the roadmap <https://github.com/andreoliwa/nitpick/projects/1>`_.

Below are the currently included plugins.

.. auto-generated-from-here

.. _iniplugin:

INI files
---------

Enforce configurations and autofix INI files.

Examples of ``.ini`` files handled by this plugin:

- `setup.cfg <https://docs.python.org/3/distutils/configfile.html>`_
- `.editorconfig <https://editorconfig.org/>`_
- `tox.ini <https://github.com/tox-dev/tox>`_
- `.pylintrc <https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options>`_

Style examples enforcing values on INI files: :gitref:`flake8 configuration
<src/nitpick/resources/python/flake8.toml>`.

.. _jsonplugin:

JSON files
----------

Enforce configurations and autofix JSON files.

Add the configurations for the file name you wish to check.
Style example: :gitref:`the default config for package.json <src/nitpick/resources/javascript/package-json.toml>`.

.. _textplugin:

Text files
----------

Enforce configuration on text files.

To check if ``some.txt`` file contains the lines ``abc`` and ``def`` (in any order):

.. code-block:: toml

    [["some.txt".contains]]
    line = "abc"

    [["some.txt".contains]]
    line = "def"

.. _tomlplugin:

TOML files
----------

Enforce configurations and autofix TOML files.

E.g.: `pyproject.toml (PEP 518) <https://www.python.org/dev/peps/pep-0518/#file-format>`_.

See also `the [tool.poetry] section of the pyproject.toml file
<https://github.com/python-poetry/poetry/blob/master/docs/pyproject.md>`_.

Style example: :gitref:`Python 3.8 version constraint <src/nitpick/resources/python/38.toml>`.
There are :ref:`many other examples here <library>`.

.. _yamlplugin:

YAML files
----------

Enforce configurations and autofix YAML files.

- Example: `.pre-commit-config.yaml <https://pre-commit.com/#pre-commit-configyaml---top-level>`_.
- Style example: :gitref:`the default pre-commit hooks <src/nitpick/resources/any/pre-commit-hooks.toml>`.

.. warning::

    The plugin tries to preserve comments in the YAML file by using the ``ruamel.yaml`` package.
    It works for most cases.
    If your comment was removed, place them in a different place of the fil and try again.
    If it still doesn't work, please :issue:`report a bug <new/choose>`.

Known issue: lists like ``args`` and ``additional_dependencies`` might be joined in a single line,
and comments between items will be removed.
Move your comments outside these lists, and they should be preserved.

.. note::

    No validation of ``.pre-commit-config.yaml`` will be done anymore in this generic YAML plugin.
    Nitpick will not validate hooks and missing keys as it did before; it's not the purpose of this package.
