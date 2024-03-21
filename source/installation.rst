==============================================================
Installation
==============================================================

.. WARNING::

    **Python Requirements**

    EMF CLI requires `Python <https://www.python.org/downloads>`_ version 3.10 or above. You also need to add it to the PATH.

Install EMF Command Line Interface
----------------------------------

You already have Go installed
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. NOTE::

    **Go Requirements**

    If you wish to install through `Go <https://go.dev/>`_, then please make sure you are using version 1.21 or above.

You can download directly using the following command
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

|:construction:| This might not work since the repository is still private |:construction:|

.. code-block:: shell

   go install github.com/easy-model-fusion/emf-cli@latest

You can also download from source
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block:: shell

   curl -L https://github.com/easy-model-fusion/emf-cli

Then build

Install manually
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To download the CLI manually, go to `EMF CLI Releases <https://github.com/easy-model-fusion/emf-cli/releases>`_ . Scroll down to the Assets section of the page and click the link (.gz or .zip) for your OS and extract the files. Make sure your system Path includes the path to the EMF CLI binary you downloaded.

**Note:** On macOS, if you’re not able to run commands, you may need to change the binary’s permissions to allow execution. From the binary’s folder, run: ``chmod 755 emf-cli``.

Verify installation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After installation, you will have access to the ``emf-cli`` binary in your command line.

You can check you have the right version with this command:

.. code-block:: sh

   emf-cli version