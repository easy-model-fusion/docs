============================================================
Basics
============================================================

Creating a project
----------------------------------

To create a new project, run :

.. code-block:: shell

   emf-cli init <project-name>

Installing an existing project
--------------------------------------

The ``emf-cli install`` command sets up the development environment for an existing EMF project based on its configuration. It prepares the project for use : installing the configured models, configuring the SDK and setting up any necessary development tools.

.. code-block:: html

    Installs an existing EMF project. Basically combining a slightly different init and the tidy commands.

    Usage:
      emf-cli install [flags]

    Flags:
      -a, --access-token string   Access token for gated models
      -c, --cuda                  Use torch with cuda
      -h, --help                  help for install

    Global Flags:
      --config-path string        config file path (default ".")

Understanding its content
--------------------------------------

Let's enter your project's folder and analyze it :

.. code-block:: shell

    awesome-ia-app/
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
If no argument is given for this command a multi-select GUI will be available in the terminal from where you can choose models to download from `models <https://huggingface.co/models>`_.

.. code-block:: html

    Add model by name to your project

    Usage:
      emf-cli model add [model name] [flags]

    Flags:
      -a, --access-token string             Access token for gated models
      -h, --help                            help for add
      -c, --model-class string              Python class within the module
      -m, --model-module string             Python module used for download
      -o, --model-options strings           List of model options
      -O, --only-configuration              Only configure the model without downloading it
      -p, --path string                     Downloaded Model directory path
      -S, --single-file                     Use the model as a single file, (usually its a safetensors file)
      -s, --skip-tokenizer                  Skip tokenizer download
      -t, --tokenizer-class string          Tokenizer class (only for transformers)
      -T, --tokenizer-options stringArray   List of tokenizer options (only for transformers)
      -y, --yes                             Automatic yes to prompts

    Global Flags:
      --config-path string                  config file path (default ".")``

    Use "emf-cli model [command] --help" for more information about a command.

You don't know which model to add? Take a look at the `Hugging Face Models page <https://huggingface.co/models>`_ or type in the following command and we will guide you through it !

.. code-block:: shell

    emf-cli model add

.. code-block:: html

You can also add a model using an existing single .safetensors file, using the `--single-file` flag.
Some other flags will be asked like the --model-class, the --path and more.

.. code-block:: shell

   emf-cli model add --single-file

Remove a model
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``emf-cli model remove`` command allows users to remove one or more models from their project. Users specify the name of the model(s) they wish to remove as command arguments. Upon execution, it removes the specified models from both the project's configuration file and the device.
If no argument is given for this command a multi-select GUI will be available in the terminal from where you can remove one or more previously downloaded models.

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
If no argument is given for this command a multi-select GUI will be available in the terminal from where you update one or more previously downloaded models.

.. code-block:: html

    Update one or more models

    Usage:
      emf-cli model update <model name> [<other model names>...] [flags]

    Flags:
      -a, --access-token string   Access token for gated models
      -h, --help                  help for update
      -y, --yes                   Automatic yes to prompts

    Global Flags:
      --config-path string        config file path (default ".")

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
        add         Add one or more tokenizers from a specific model
        remove      Remove one or more tokenizers from a specific model
        update      Update one or more tokenizers from a specific model

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

    Add tokenizer by class to your model

    Usage:
         emf-cli tokenizer add <model name> <tokenizer name> [flags]

    Flags:
        -c, --class string          Tokenizer class
        -h, --help                  help for add
        -o, --options stringArray   List of tokenizer options

    Global Flags:
        --config-path string             config file path (default ".")

Remove a tokenizer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``emf-cli tokenizer remove`` command allows users to remove one or more `tokenizers <https://huggingface.co/docs/transformers/main_classes/tokenizer>`_ from their project. Users specify the name of the model associated with the tokenizer and the tokenizer name(s) they wish to remove as command arguments.
If no argument is given for this command a multi-select GUI will be available in the terminal from where you remove one or more previously downloaded model tokenizers.

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
If no argument is given for this command a multi-select GUI will be available in the terminal from where you update one or more previously downloaded model tokenizers.

.. code-block:: html

    Update one or more tokenizer

    Usage:
         emf-cli tokenizer update <model name> <tokenizer name> [<other tokenizer names>...] [flags]

    Flags:
        -h, --help   help for update

    Global Flags:
        --config-path string             config file path (default ".")

Manipulating options
----------------------------------

When specifying options with ``--model-options`` or ``--tokenizer-options``, things might be a bit tricky so let's go through the different formats and examples to ensure clarity and accuracy.

Default
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When working with default values, you just have to use the following format :

.. code-block:: html

    --model-options key=module.value
    --model-options key=True
    --model-options key=123456789

Multiple options
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You could simply specify the flag as many times as needed :

.. code-block:: html

    --model-options key1=value1 --model-options key2=value2 --model-options key3=value3

Or you could put them side by side and encapsulate them into double quotes :

.. code-block:: html

    --model-options "key1=value1 key2=value2 key3=value3"

Strings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In shell scripting or command-line interfaces, quoting strings is crucial to prevent interpretation or expansion by the shell. Without quoting, certain characters or sequences might be treated specially, leading to unintended behavior :

.. code-block:: html

    --model-options "key='value'"
    --model-options key="'value'"

Now here is how it looks like when combining with multiple options :

.. code-block:: html

    --model-options "key1='value1' key2='value2' key3='value3'"
    --model-options key="'value'"

Project synchronization (tidy)
----------------------------------

.. warning::

    Please be aware that it is currently not possible to retrieve the version or the options used while handling downloaded but not configured models.

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
      -a, --access-token string   Access token for gated models
      -h, --help                  help for tidy
      -y, --yes                   Automatic yes to prompts

    Global Flags:
      --config-path string        config file path (default ".")

Building a project
----------------------------------

The ``emf-cli build`` command facilitates the process of building the project. It compiles the project's source code and dependencies into an executable format suitable for deployment or distribution.

Upon execution, the command offers various options to customize the build process:
    - ``-l, --library string``: Specifies the library to use for building the project. Users can select between "pyinstaller" and "nuitka". The default is "pyinstaller".
    - ``-s, --models-symlink``: Creates a symlink for the models directory in the build directory.
    - ``-n, --name string``: Allows users to specify a custom name for the executable.
    - ``-f, --one-file``: Builds the project in one file, consolidating all dependencies and resources into a single executable file.
    - ``-o, --out-dir string``: Specifies the destination directory where the project will be built. The default is "dist".

.. code-block:: html

    Build the project.

    Usage:
         emf-cli build [flags]

    Flags:
        -h, --help             help for build
        -l, --library string   Library to use for building the project (select between pyinstaller and nuitka) (default "pyinstaller")
        -s, --models-symlink   Symlink the models directory to the build directory
        -n, --name string      Custom name for the executable
        -f, --one-file         Build the project in one file
        -o, --out-dir string   Destination directory where the project will be built (default "dist")

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
