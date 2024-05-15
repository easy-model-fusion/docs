==============================================================
Installation
==============================================================

.. WARNING::

    **Python Requirements**

    EMF CLI requires `Python <https://www.python.org/downloads>`_ version >3.10.4 and <3.12. The optimal version would be the 3.11, that is also the version we used for development. You also need to add it to the PATH.

Install EMF Command Line Interface
----------------------------------

Install manually
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To download the CLI manually, go to `EMF CLI Releases <https://github.com/easy-model-fusion/emf-cli/releases>`_ . Scroll down to the Assets section of the page and click the link (.gz or .zip) for your OS and extract the files. Make sure your system Path includes the path to the EMF CLI binary you downloaded.

**Note:** On macOS, if you’re not able to run commands, you may need to change the binary’s permissions to allow execution. From the binary’s folder, run: ``chmod 755 emf-cli``.

Install using Go
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. NOTE::

    **Go Requirements**

    If you wish to install through `Go <https://go.dev/>`_, then please make sure you are using version 1.21 or above.

Install it directly using the following command
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

|:construction:| This might not work since the repository is still private |:construction:|

.. code-block:: shell

   go install github.com/easy-model-fusion/emf-cli@latest

Install it from source
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

First get the source code from the repository :

.. code-block:: shell

   git clone https://github.com/easy-model-fusion/emf-cli
   cd emf-cli/

Then you can start building (using make) :

.. code-block:: shell

   make build

Or you could also build it yourself :

.. code-block:: shell

   go build

Now all that's left for you is adding it to the PATH !

Verify installation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After installation, you will have access to the ``emf-cli`` binary in your command line.

You can check you have the right version with this command:

.. code-block:: sh

   emf-cli version
