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

Model manager : With vs. Without
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Utilizing the model manager component of the SDK offers several advantages over manually managing models:

- **Simplified model management** : it provides a centralized interface to manage all instantiated models. Without it, developers would need to handle model loading, unloading and prompt generation manually, leading to more complex and error-prone code.
- **Improved resource management** : it ensures efficient use of system resources by handling the loading and unloading of models as needed. This helps prevent memory leaks and ensures optimal performance of your application.
- **Enhanced productivity** : By abstracting away low-level model management tasks, it allows developers to focus on building innovative AI applications rather than dealing with infrastructure concerns.

Upgrading the SDK
----------------------------------

This command checks for updates from the EMF repository and handles the upgrade process automatically, keeping the toolkit up-to-date with the latest developments.

.. code-block:: sh

   emf-cli upgrade