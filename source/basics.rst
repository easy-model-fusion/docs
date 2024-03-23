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

The ``emf-cli install`` command sets up the development environment for an existing EMF project based on its configuration. It prepares the project for use : installing the configured models, configuring the SDK and setting up any necessary development tools.

.. code-block:: html

    Installs an existing EMF project. Basically combining a slightly different init and the tidy commands.

    Usage:
         emf-cli install [flags]

    Flags:
        -c, --cuda   Use torch with cuda
        -h, --help   help for install

    Global Flags:
        --config-path string             config file path (default ".")

Understanding its content
--------------------------------------

Let's enter you project's folder and analyze it :

.. code-block:: shell

    awesome-ia-app
    ├── .venv/
    ├── dist/
    ├── models/
    ├── sdk/
    ├── config.yaml
    ├── main.py

* ``.venv/`` encapsulates all Python dependencies required by the project, ensuring a clean and isolated environment for development.
* ``dist/`` contains the distribution files of your project, which includes the executable or packaged files ready for deployment.
* ``models/`` contains the downloaded `models <https://huggingface.co/models>`_ to be used in the project.
* ``sdk/`` contains essential tools and resources tailored for the project's development needs. For more details, refer to the :doc:`Development <development>` page.
* ``config.yaml`` centralizes application settings, enabling user customization for behavior and AI model selection. For more details, refer to the :doc:`Configuration Reference <config-yaml>` page.
* ``main.py`` is where the magic happens : it serves as the heart of your application and showcases the full capabilities of the EMF toolkit.

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

| The ``emf-cli model add`` command allows users to add a model to their project by specifying the model name and optional configuration flags.
| For more information on available models, visit the `Hugging Face Models page <https://huggingface.co/models>`_.

.. code-block:: html

    Add model by name to your project

    Usage:
         emf-cli model add [model name] [flags]

    Flags:
        -h, --help                            help for add
        -c, --model-class string              Python class within the module
        -m, --model-module string             Python module used for download
        -o, --model-options strings           List of model options
        -p, --path string                     Downloaded Model directory path
        -s, --skip string                     Skip the model or tokenizer download
        -t, --tokenizer-class string          Tokenizer class (only for transformers)
        -T, --tokenizer-options stringArray   List of tokenizer options (only for transformers)
        -y, --yes                             Automatic yes to prompts

    Global Flags:
        --config-path string             config file path (default ".")

    Use "emf-cli model [command] --help" for more information about a command.

Remove a model
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``emf-cli model remove`` command allows users to remove one or more models from their project. Users specify the name of the model(s) they wish to remove as command arguments. Upon execution, it removes the specified models from both the project's configuration file and the device.

.. code-block:: html

    Remove one or more models

    Usage:
         emf-cli model remove <model name> [<other model names>...] [flags]

    Flags:
        -a, --all    Remove all models
        -h, --help   help for remove

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
        -h, --help   help for update

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

.. note::

    A recommended tokenizer should already be downloaded by default upon adding a model with the ``emf-cli model add`` command. Users can verify the configured models in the configuration file. If the downloaded tokenizer does not meet the user's preferences, they are welcome to add one of their choice.

.. code-block:: html

    Add one or more tokenizer

    Usage:
         emf-cli tokenizer add <model name> <tokenizer name> [<other tokenizer names>...] [flags]

    Flags:
        -h, --help   help for add

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
        -h, --help   help for remove

    Global Flags:
        --config-path string             config file path (default ".")

Update a tokenizer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. warning::

    It currently cannot be determined if a tokenizer can be updated. Therefore, we created this command to allow you to redownload a tokenizer if you have learned that a new version is available.

The ``emf-cli tokenizer update`` command allows users to update one or more `tokenizers <https://huggingface.co/docs/transformers/main_classes/tokenizer>`_ from their project. Users specify the name of the model associated with the tokenizer and the tokenizer name(s) they wish to update as command arguments.

.. code-block:: html

    Update one or more tokenizer

    Usage:
         emf-cli tokenizer update <model name> <tokenizer name> [<other tokenizer names>...] [flags]

    Flags:
        -h, --help   help for update

    Global Flags:
        --config-path string             config file path (default ".")

Project synchronization (tidy)
----------------------------------

The ``emf-cli tidy`` command synchronizes the project's configuration file with the downloaded models. It ensures consistency between the configured models in the project's configuration file and the actual downloaded models on the device.

Upon execution, the command performs the following tasks:

- Removes any configured models that are not downloaded, ensuring that the configuration file accurately reflects the current state of downloaded models.
- Offers options to either download or remove any downloaded models that are not configured in the configuration file, providing users with the flexibility to manage downloaded models as needed.

This command aids in maintaining an organized and up-to-date model repository, facilitating efficient management of models within the project.

.. code-block:: html

    Synchronizes the configuration file with the downloaded models

    Usage:
         emf-cli tidy [flags]

    Flags:
        -h, --help   help for tidy

    Global Flags:
        --config-path string             config file path (default ".")

Building a project
----------------------------------

The ``emf-cli build`` command facilitates the process of building the project. It compiles the project's source code and dependencies into an executable format suitable for deployment or distribution.

Upon execution, the command offers various options to customize the build process:
    - ``-c, --compress``: Compresses the output file(s) into a tarball file for easy distribution.
    - ``-m, --include-models``: Includes models in the build compressed file, allowing for bundled distribution of models with the project.
    - ``-n, --name string``: Allows users to specify a custom name for the executable.
    - ``-f, --one-file``: Builds the project in one file, consolidating all dependencies and resources into a single executable file.
    - ``-o, --out-dir string``: Specifies the destination directory where the project will be built.

.. code-block:: html

    Build the project.

    Usage:
         emf-cli build [flags]

    Flags:
        -c, --compress         Compress the output file(s) into a tarball file
        -h, --help             help for build
        -m, --include-models   Include models in the build compressed file
        -n, --name string      Custom name for the executable
        -f, --one-file         Build the project in one file
        -o, --out-dir string   Destination directory where the project will be built

    Global Flags:
        --config-path string             config file path (default ".")

Cleaning a project
----------------------------------

The ``emf-cli clean`` command allows users to clean project files. The cleaning operation removes build files and, optionally, all downloaded models associated with the project.

.. code-block:: html

    Clean project files (e.g. build)

    Usage:
         emf-cli clean [flags]

    Flags:
        -a, --all    clean all project
        -h, --help   help for clean
        -y, --yes    bypass delete all confirmation

    Global Flags:
        --config-path string             config file path (default ".")