---
description: 'TL;DR: Do `pip install zenml` to install.'
---

# Installation

## Welcome

Your first step is to install **ZenML**, which comes bundled as a good old `pip` package. 

{% hint style="warning" %}
Please note that we only support Python &gt;= 3.6, so please adjust your pip accordingly.
{% endhint %}

## Virtual Environment

We highly encourage you to install **ZenML** in a virtual environment. We install dependencies like `PyArrow` and `Tensorflow` that might cause your base installations to be overridden.

We like to use [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/) to manage our Python virtual environments.

## Install with pip

When you're set with your environment, run:

```bash
pip install zenml
```

Alternatively, if you’re feeling brave, feel free to install the bleeding edge: **NOTE:** Do so at your own risk, no guarantees given!

```bash
pip install git+https://github.com/maiot-io/zenml.git@main --upgrade
```

## Integrations

The **ZenML** base package does not come up with all integrations pre-installed. Read more [here](advanced-guide/integrations.md). In order to install an integration, use the pattern:

```bash
pip install zenml[INTEGRATION]
```

e.g.

```bash
pip install zenml[pytorch]
```

Use the keyword `all` in the square brackets if you would like to install all integrations.

Once the installation is completed, you can check whether the installation was successful through:

### Bash

```bash
zenml version
```

### Python

```python
import zenml
print(zenml.utils.version.__version__)
```

If you would like to learn more about the current release, please visit the [PyPi homepage.](https://pypi.org/project/zenml)

## Enabling auto-completion on the CLI

For Bash, add this to `~/.bashrc`:

```bash
eval "$(_ZENML_COMPLETE=source_bash zenml)"
```

For Zsh, add this to `~/.zshrc`:

```bash
eval "$(_ZENML_COMPLETE=source_zsh zenml)"
```

For Fish, add this to `~/.config/fish/completions/foo-bar.fish`:

```bash
eval (env _ZENML_COMPLETE=source_fish zenml)
```

## Tensorflow Model Analysis \(TFMA\) support

In order to get the [Tensorflow Model Analysis](https://github.com/tensorflow/model-analysis) evaluation visualizations to work, you must also run:

```bash
jupyter nbextension install --py --symlink tensorflow_model_analysis
jupyter nbextension enable --py tensorflow_model_analysis
```

{% hint style="warning" %}
If you encounter a `File already exists in database` error after the first command, this is most likely due to a [known bug](https://stackoverflow.com/questions/59165505/file-already-exists-in-database-error-from-protobuf-when-deploying-google-datafl) with one of our dependencies, namely [PyArrow](https://pypi.org/project/pyarrow/). Unfortunately, this will cause some features to not work on your machine namely **evaluate** and **compare**.

We are aware of this issue and are working hard to fix it. A future release of **ZenML** will fix this issue.
{% endhint %}

