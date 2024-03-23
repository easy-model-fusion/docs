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
* ``models/`` contains the downloaded `models <https://huggingface.co/models>`_ to be used in the project.
* ``sdk/`` contains essential tools and resources tailored for the project's development needs. For more details, refer to the :doc:`Development <development>` page.
* ``config.yaml`` centralizes application settings, enabling user customization for behavior and AI model selection. For more details, refer to the :doc:`Configuration Reference <config-yaml>` page.
* ``main.py`` **???**

Working with models
----------------------------------

When working with `models <https://huggingface.co/models>`_, you will be using the ``emf-cli model`` command :

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

.. WARNING::

    Please note that we currently support the following model types:
        - single file models
        - `diffusers <https://huggingface.co/diffusers>`_ models
        - `transformers <https://huggingface.co/docs/transformers/index>`_ models

    Please ensure that the models you intend to use adhere to these specifications. Using unsupported models may lead to unexpected behavior or errors in the application.

|:construction:| WIP |:construction:|

`models <https://huggingface.co/models>`_

Remove a model
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``emf-cli model remove`` command allows users to remove one or more models from their project. Users specify the name of the model(s) they wish to remove as command arguments. Upon execution, it removes the specified models from both the project's configuration file and the device.

.. code-block:: html

    Remove one or more models

    Usage:
         emf-cli model remove <model name> [<other model names>...] [flags]

    Flags:
        -a, --all    Remove all models
        -h, --help   help for model

    Global Flags:
        --config-path string             config file path (default ".")

Update a model
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``emf-cli model update`` command allows users to update one or more models from their project. Users specify the name of the model(s) they wish to update as command arguments. This command will only update models sourced from `Hugging Face <https://huggingface.co/>`_ and if a newer version is available (determined through the `Hugging Face API <https://huggingface.co/docs/hub/api>`_).

.. code-block:: html

    Update one or more models

    Usage:
         emf-cli model update <model name> [<other model names>...] [flags]

    Flags:
        -h, --help   help for model

    Global Flags:
        --config-path string             config file path (default ".")

Working with tokenizers
----------------------------------

.. WARNING::

    **Tokenizer Requirements**

    `Tokenizers <https://huggingface.co/docs/transformers/main_classes/tokenizer>`_ are only available for models sourced from `Hugging Face's Transformers <https://huggingface.co/docs/transformers/index>`_ library. Please ensure that you are using a compatible model type when requesting tokenizers. Using incompatible models may result in unexpected behavior or errors in your application.

When working with `tokenizers <https://huggingface.co/docs/transformers/main_classes/tokenizer>`_, you will be using the ``emf-cli tokenizer`` command :

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

The ``emf-cli tokenizer add`` command allows users to add one or more `tokenizers <https://huggingface.co/docs/transformers/main_classes/tokenizer>`_ to their project. Users specify the name of the model associated with the tokenizer and the tokenizer name(s) they wish to add as command arguments.

.. code-block:: html

    Add one or more tokenizer

    Usage:
         emf-cli tokenizer add <model name> <tokenizer name> [<other tokenizer names>...] [flags]

    Flags:
        -h, --help   help for model

    Global Flags:
        --config-path string             config file path (default ".")

Remove a tokenizer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``emf-cli tokenizer remove`` command allows users to remove one or more `tokenizers <https://huggingface.co/docs/transformers/main_classes/tokenizer>`_ from their project. Users specify the name of the model associated with the tokenizer and the tokenizer name(s) they wish to remove as command arguments.

.. code-block:: html

    Remove one or more tokenizer

    Usage:
         emf-cli tokenizer remove <model name> <tokenizer name> [<other tokenizer names>...] [flags]

    Flags:
        -h, --help   help for model

    Global Flags:
        --config-path string             config file path (default ".")

Update a tokenizer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``emf-cli tokenizer update`` command allows users to update one or more `tokenizers <https://huggingface.co/docs/transformers/main_classes/tokenizer>`_ from their project. Users specify the name of the model associated with the tokenizer and the tokenizer name(s) they wish to update as command arguments. Please note that, as of today, it cannot be determined if a tokenizer can be updated. Therefore, we created this command to allow you to redownload a tokenizer if you have learned that a new version is available.

.. code-block:: html

    Update one or more tokenizer

    Usage:
         emf-cli tokenizer update <model name> <tokenizer name> [<other tokenizer names>...] [flags]

    Flags:
        -h, --help   help for model

    Global Flags:
        --config-path string             config file path (default ".")


Building a project
----------------------------------

To create a new project, run:

Others
----------------------------------

To create a new project, run: