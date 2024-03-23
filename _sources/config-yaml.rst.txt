=======================
Configuration Reference
=======================

The ``config.yaml`` file serves as a centralized configuration hub for the application, allowing users to specify various parameters and settings tailored to their requirements. It facilitates customization of the application's behavior, including the selection and configuration of AI models. Users can modify the configuration file to adapt the application to different environments and use cases, enhancing flexibility and versatility.


Application Information
-----------------------------------

- **name**: The name of the application.
- **version**: The version of the application.
- **description**: A brief description of the application.

SDK Configuration
-----------------------------------

- **sdk-tag**: The version of the SDK to download.

Model Configuration
-----------------------------------

.. NOTE::

    When manipulating configured models, please refer to the :doc:`Basics <basics>` page for detailed instructions and best practices.

The ``models`` section allows users to specify AI models to be used in the application. Each model configuration includes the following parameters:

- **name**: The name of the model.
- **path**: The path of the directory that will contain the model.
- **module**: The Python module used for downloading the model.
- **class**: The Python class within the module.
- **options**: A map of additional options for configuring the model.
- **tokenizers**: List of tokenizer configurations.

    - **path**: The path of the directory that will contain the tokenizer.
    - **class**: The Python class used for downloading the tokenizer.
    - **options**: A map of additional options for configuring the tokenizer.
- **pipelinetag**: The pipeline tag used by the model identifies the specific task or functionality supported by the model (e.g., text-to-image, text-generation).
- **source**: The source of the model (e.g., hugging_face).
- **addtobinaryfile**: Indicates if the model should be added to the executable.
- **isdownloaded**: Indicates if the model has been downloaded.
- **version**: The version of the model.

Example
-----------------------------------

.. code-block:: yaml

    # Application information
    name: "awesome-ia-app"
    version: "1.0.0"
    description: "Description for your awesome IA application."

    # SDK Configuration
    sdk-tag: "vX.Y.Z"

    # Model Configuration
    models:

        # Diffusers model
        - name: stabilityai/sdxl-turbo
            path: models/stabilityai/sdxl-turbo
            module: diffusers
            class: StableDiffusionXLPipeline
            options:
                torch_dtype: torch.float16
            tokenizers: []
            pipelinetag: text-to-image
            source: hugging_face
            addtobinaryfile: false
            isdownloaded: false
            version: "2023-12-07T18:04:49.000Z"

        # Transformers model
        - name: microsoft/phi-2
            path: models/microsoft/phi-2/model
            module: transformers
            class: PhiModel
            options:
                torch_dtype: '"auto"'
            tokenizers:
                - path: models\microsoft\phi-2\AutoTokenizer
                    class: AutoTokenizer
                    options:
                        do_lower_case: "True"
                        max_len: "128"
            pipelinetag: text-generation
            source: hugging_face
            addtobinaryfile: true
            isdownloaded: true
            version: "2024-02-06T12:36:24.000Z"
