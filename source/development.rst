===================================================
Development
===================================================

Here, we provide comprehensive guidance and resources to empower developers in creating and managing AI-powered applications with ease and efficiency.

Understanding its content
--------------------------------------

.. warning::

    Be aware that editing these files directly may lead to unexpected behaviors or errors. It's recommended to interact with these files only through the provided interfaces and commands.

Let us enter the SDK and take a look at it to understand how it works :

.. code-block:: shell

    sdk/
    ├── demo/
    ├── models/
    ├── tests/
    ├── downloader.py
    ├── generated_models.py

* ``demo/`` contains demonstration scripts showcasing the functionality of the SDK and how it interacts with AI models
* ``models/`` contains base classes serving as the foundation for each installed AI model. These base classes provide common functionalities and interfaces that the generated classes extend or implement. They ensure consistency and interoperability across different AI models
* ``tests/`` contains test suites to ensure the reliability of the SDK's functionalities
* ``downloader.py`` is the script used by the :doc:`EMF CLI <basics>` to download models and tokenizers
* ``generated_models.py`` is a dynamic file containing the generated classes for each AI model configured. This file simplifies the integration process by providing developers with pre-defined interfaces to interact with the models they installed

Using the SDK
--------------------------------------

The EMF SDK offers a streamlined approach to integrate AI models into your applications effortlessly. Understanding how to leverage its features can significantly enhance your development workflow.

Adding models
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The first step is adding models to your project using the :doc:`EMF CLI <basics>`. Once added, these models are automatically generated into the ``generated_models.py`` file. This file contains pre-defined interfaces for each installed model, making it easy to interact with them in your code.

Setting up the file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

| To begin using the SDK, you'll first need to locate the ``main.py`` file adjacent to the ``sdk/`` folder within your EMF project.
| Then you will be able to import the EMF SDK it into your project. This can be done by adding the following line at the beginning of the file :

.. code-block:: shell

    import sdk

Using a model class
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Instantiating a model
========================================================

Now that you've set up the file, all that's left for you to do is instantiating your model :

.. code-block:: python

    # Assuming the name for the generated class is : NameOfYourAutoGeneratedModelClass
    model = sdk.NameOfYourAutoGeneratedModelClass()

The models' device by default is ``GPU`` but if you wish to load a model onto the ``CPU`` :

.. code-block:: python

    model.device = "CPU"

.. _loading-model-class:

Loading onto a device
========================================================

This function is responsible for loading the model onto its specified device which is required for :ref:`generating prompts <generating-prompt-model-class>`.

.. warning::

    Developers need to verify that the designated device possesses adequate storage capacity to accommodate the model, especially if you are planning to load multiple models onto the same device. They also need to ensure that the device is compatible with the loaded model.

.. note::

    Loading large models or multiple models simultaneously can consume significant system resources, such as memory and processing power. Developers should be mindful of resource usage and optimize the loading process accordingly.

.. code-block:: python

    model.load_model()

.. _unloading-model-class:

Unloading from the device
========================================================

This function is responsible for unloading the model from its specified device. It allows developers to free up memory and system resources by unloading models that are no longer needed or in use by the application.

.. code-block:: python

    model.unload_model()

.. _generating-prompt-model-class:

Generating a prompt
========================================================

This function is responsible for generating prompts.

.. warning::

    Please ensure that the selected model has been loaded onto a device before trying to generate a prompt.

.. code-block:: python

    model.generate_prompt(prompt, **kwargs)

Using the model manager
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The **ModelsManagement** class serves as the central control hub for managing all instantiated models within the application. It becomes particularly useful when manipulating multiple models.

It provides several advantages over manually managing models :

- **Simplified model management** : it provides a centralized interface to manage all instantiated models. Without it, developers would need to handle model loading, unloading and prompt generation separately, leading to more complex and error-prone code.
- **Improved resource management** : it ensures efficient use of system resources by handling the loading and unloading of models as needed. This helps prevent memory leaks and ensures optimal performance of your application.
- **Enhanced productivity** : By abstracting away low-level model management tasks, it allows developers to focus on building innovative AI applications rather than dealing with infrastructure concerns.

To instantiate it, use the following :

.. code-block:: python

    model_management = ModelsManagement()

Adding a new model to the management system
========================================================

By adding models to the manager, developers can centrally manage all instantiated models within the application. This helps maintain consistency and simplifies the overall model management process.

.. code-block:: python

    # Assuming the name for the generated class is : NameOfYourAutoGeneratedModelClass
    model = sdk.NameOfYourAutoGeneratedModelClass()
    model_management.add_model(model)

Loading a specified model onto a device
========================================================

This function is responsible for loading a specified model onto its specified device. It allows developers to select a specific model from the pool of available models and load it into memory. This is essential for applications that require the use of multiple models, as it allows developers to dynamically switch between models based on user input or other factors.

It basically executes the ``load_model()`` function for the selected :ref:`model class <loading-model-class>`.

.. code-block:: python

    model_management.load_model(model.model_name)

Unloading the currently loaded model from the device
========================================================

This function is responsible for unloading the currently loaded model from its specified device. It basically executes the ``unload_model()`` function for the currently loaded :ref:`model class <unloading-model-class>`.

.. code-block:: python

    model_management.unload_model()

Generating a prompt
========================================================

This function is responsible for generating prompts.

.. note::

    If the model is currently loaded, there is no need to provide the ``model_name`` argument. If the chosen model has yet to be loaded, it will first unload the current model from the specified device (if any), load the model and then generate the prompt.

It basically executes the ``generate_prompt()`` function for the selected :ref:`model class <generating-prompt-model-class>`.

.. code-block:: python

    model_management.generate_prompt(prompt, model_name=model.model_name, **kwargs)

Examples
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can find real use cases in the :doc:`Examples <examples>` section.


Upgrading the SDK
----------------------------------

This command checks for updates from the EMF repository and handles the upgrade process automatically, keeping the toolkit up-to-date with the latest developments.

.. code-block:: sh

   emf-cli upgrade