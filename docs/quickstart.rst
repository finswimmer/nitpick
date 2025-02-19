.. include:: targets.rst

Quickstart
==========

Install
-------

Install in an isolated environment with pipx_::

    # Latest PyPI release
    pipx install nitpick

    # Development branch from GitHub
    pipx install git+https://github.com/andreoliwa/nitpick

On macOS/Linux, install the latest release with Homebrew_::

    brew install andreoliwa/formulae/nitpick

    # Development branch from GitHub
    brew install andreoliwa/formulae/nitpick --HEAD

On Arch Linux, install with yay::

    yay -Syu nitpick

Add to your project with Poetry_::

    poetry add --dev nitpick

Or install it with pip::

    pip install -U nitpick

Run
---

To fix and modify your files directly::

    nitpick fix

To check for errors only::

    nitpick check

Nitpick is also a flake8_ plugin, so you can run this on a project with at least one Python (``.py``) file::

    flake8 .

Nitpick_ will download and use the opinionated :gitref:`default style file <nitpick-style.toml>`.

You can use it as a template to :ref:`configure-your-own-style`.

Run as a pre-commit hook
------------------------

If you use pre-commit_ on your project, add this to the ``.pre-commit-config.yaml`` in your repository:

.. code-block:: yaml

    repos:
      - repo: https://github.com/andreoliwa/nitpick
        rev: v0.32.0
        hooks:
          - id: nitpick

There are 3 available hook IDs:

- ``nitpick`` and ``nitpick-fix`` both run the ``nitpick fix`` command;
- ``nitpick-check`` runs ``nitpick check``.

If you want to run Nitpick_ as a flake8_ plugin instead::

    repos:
      - repo: https://github.com/PyCQA/flake8
        rev: 4.0.1
        hooks:
          - id: flake8
            additional_dependencies: [nitpick]

To install the ``pre-commit`` and ``commit-msg`` Git hooks:

.. code-block:: shell

    pre-commit install --install-hooks
    pre-commit install -t commit-msg

To start checking all your code against the default rules:

.. code-block:: shell

    pre-commit run --all-files

Run as a MegaLinter plugin
---------------------------

If you use `MegaLinter <https://megalinter.github.io/>`_ you can run Nitpick as a plugin. Add the following two entries to your ``.mega-linter.yml`` configuration file:

.. code-block:: yaml

    PLUGINS:
      - https://raw.githubusercontent.com/andreoliwa/nitpick/v0.32.0/mega-linter-plugin-nitpick/nitpick.megalinter-descriptor.yml
    ENABLE_LINTERS:
      - NITPICK

Modify files directly
---------------------

Nitpick_ includes a CLI to apply your style and modify the configuration files directly:

.. code-block:: shell

    nitpick fix

Read more details here: :ref:`cli`.
