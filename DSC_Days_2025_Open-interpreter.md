# Using Open Interpreter as a personal coding and data analysis
assistant

January 8, 2025

## Installation instructions

- use Python 3.10 or 3.11, not higher (!)

## Installation instructions

It is highly recommended to use an environment for Python:

- conda
- python virtual environment

## conda installation

``` .bash
conda create --name open-interpreter python=3.11
conda activate open-interpreter[local]
conda install pip
pip install open-interpreter
interpreter --version
```

**TIP** Make some copies of this environment, this will be useful for
later

``` .bash
conda create --name open-interpreter2 --clone open-interpreter
```

## python virtual env installation

``` .bash
python -m venv /path/to/open-interpreter
source /path/to/open-interpreter
pip install open-interpreter[local]
interpreter --version
```

**TIP** Make some more instances of this environment, this will be
useful for later

``` .bash
python -m venv /path/to/open-interpreter2
```

## Using a local model

``` .bash
interpreter --local

Open Interpreter supports multiple local model providers.

[?] Select a provider:
   Ollama
 > Llamafile
   LM Studio
   Jan

[?] Select a model:
 > ↓ Download new model
```

Choose `Llama-3.1-8B-Instruct`

## Exercise

Get it to write some code

## etc

You can modify the max_tokens and context_window (in tokens) of locally
running models.

For local mode, smaller context windows will use less RAM, so we
recommend trying a much shorter window (~1000) if it’s failing / if it’s
slow. Make sure max_tokens is less than context_window.

interpreter –local –max_tokens 1000 –context_window 3000
