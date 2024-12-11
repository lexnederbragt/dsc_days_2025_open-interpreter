# Using Open Interpreter as a personal coding and data analysis assistant

## Installation instructions

- use Python 3.10 or 3.11, not higher (!)

It is highly recommended to use an environment for Python.

Choose between

- conda
- python virtual environment

## installation using conda

``` .bash
conda create --name open-interpreter python=3.11
conda activate open-interpreter
pip install open-interpreter[local]
interpreter --version
```

**TIP** Make some copies of this environment, this will be useful for
later

In another terminal, write

``` .bash
conda create --name open-interpreter2 --clone open-interpreter
```

## Installation using python virtual env

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

## What did we install

``` .bash
conda env export --from-history
```

## Using a local model

Start Open Interpreter with

``` .bash
interpreter --local
```

Now select `Llamafile`

    Open Interpreter supports multiple local model providers.

    [?] Select a provider:
       Ollama
     > Llamafile
       LM Studio
       Jan

    [?] Select a model:
     > ↓ Download new model

Choose `Llama-3.1-8B-Instruct`

## Our first program

Ask:

> Write a program that casts a die 1000 times and determines the
> frequency of sixes

Then ask

> What is the expected frequency?

<!-- 
&#10;## Exercise 
&#10;Get it to write some code
&#10;
&#10;## etc
&#10;You can modify the max_tokens and context_window (in tokens) of locally running models.
&#10;For local mode, smaller context windows will use less RAM, so we recommend trying a much shorter window (~1000) if it's failing / if it's slow. Make sure max_tokens is less than context_window.
&#10;interpreter --local --max_tokens 1000 --context_window 3000
&#10; -->
