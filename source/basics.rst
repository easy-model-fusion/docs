============================================================
Basics
============================================================

Creating a project
----------------------------------

To create a new project, run :

.. code-block:: shell

   emf-cli init awesome-ia-app

Installing an existing project
--------------------------------------

|:construction:| WIP |:construction:|

Understanding its content
--------------------------------------

Let's enter you project's folder and analyze it :

.. code-block:: shell

    awesome-ia-app
    ├── .venv/
    ├── models/
    ├── sdk/
    ├── config.yaml
    ├── main.py

* ``.venv/`` encapsulates all Python dependencies required by the project, ensuring a clean and isolated environment for development.
* ``models/`` contains the downloaded models to be used in the project.
* ``sdk/`` contains essential tools and resources tailored for the project's development needs. For more details, refer to the :doc:`Development <development>` page.
* ``config.yaml`` centralizes application settings, enabling user customization for behavior and AI model selection. For more details, refer to the :doc:`Configuration Reference <config-yaml>` page.
* ``main.py`` **???**

Working with models
----------------------------------

When working with models, you will be using ``emf-cli model`` :

.. code-block:: html

    Palette that contains model based commands

    Usage:
        emf-cli model [flags]
        emf-cli model [command]

    Available Commands:
        add         Add model by name to your project
        remove      Remove one or more models
        update      Update one or more models

    Flags:
        -h, --help   help for model

    Global Flags:
        --config-path string             config file path (default ".")

    Use "emf-cli model [command] --help" for more information about a command.

Adding a model
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Adding a model

Remove a model
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Remove a model

Update a model
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Update a model

Working with tokenizers
----------------------------------

When working with tokenizers, you will be using ``emf-cli tokenizer`` :

.. code-block:: html

    Palette that contains tokenizer based commands

    Usage:
        emf-cli tokenizer [flags]
        emf-cli tokenizer [command]

    Available Commands:
        add         Add one or more tokenizers
        remove      Remove one or more tokenizers
        update      Update one or more tokenizers

    Flags:
        -h, --help   help for tokenizer

    Global Flags:
        --config-path string             config file path (default ".")

    Use "emf-cli tokenizer [command] --help" for more information about a command.

Adding a tokenizer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Adding a tokenizer

Remove a tokenizer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Remove a tokenizer

Update a tokenizer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Update a tokenizer


Building a project
----------------------------------

To create a new project, run:

Others
----------------------------------

To create a new project, run: