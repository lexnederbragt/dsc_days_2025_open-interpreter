# Using Open Interpreter as a personal coding and data analysis assistant

January 8, 2025

## About this workshop

The goals

- Used Open Interpreter for some tasks
- Be inspired to use it more
- Be aware of pitfalls and challenges

## Caveats

- Installation may be problematic for some

<div class="incremental">

- The program may at times be a bit buggy
- The workshop may run smooth - or not

</div>

## Installation instructions

- use Python 3.10 or 3.11, not higher (!)

It is highly recommended to use an environment for Python.

Choose between

- conda
- python virtual environment

## Installation using conda

``` .bash
conda create --name open-interpreter python=3.11
conda activate open-interpreter
pip install "open-interpreter[local]"
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
pip install "open-interpreter[local]"
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

## Our first task

Ask:

> Write a program that casts a die 1000 times and determines the
> frequency of sixes

Then ask

> What is the expected frequency?

## Settings

From
https://github.com/OpenInterpreter/open-interpreter/blob/main/README.md#context-window-max-tokens

> For local mode, smaller context windows will use less RAM, so we
> recommend trying a much shorter window (~1000) if it’s failing / if
> it’s slow. Make sure max_tokens is less than context_window.

``` .bash
interpreter --local --max_tokens 1000 --context_window 3000
```

If you see a warning at first use around `LiteLLM:ERROR:`, add this to
your `interpreter` command:

    --no-llm_supports_functions

## Another task

> Write a program that casts two dice 1000 times and plots the
> distribution of the sum of the casts.

## Other ways to use a local model

Find the location of the model files

``` .bash
interpreter --local_models
```

Now start the model server in a different terminal instance.

On Mac:

``` .bash
cd ~/Library/Application\ Support/open-interpreter/models/
./Meta-Llama-3.1-8B-Instruct.Q4_K_M.llamafile
```

    software: llamafile 0.8.15
    model:    Meta-Llama-3.1-8B-Instruct.Q4_K_M.gguf
    compute:  Apple Metal GPU
    server:   http://127.0.0.1:8080/

Feel free to chat with the model ;-)

Now you can use this server with Open-Interpreter:

``` .bash
interpreter --api_base http://127.0.0.1:8080/v1
```

Alternatively:

``` .bash
interpreter --api_base http://localhost:8080/v1 -m llamafile -ak dummykey
```

## We need a bigger model

``` .bash
interpreter --model gpt-4o -ak YOUR_OPENAI_API_KEY
```

For other providers, see
<https://docs.openinterpreter.com/language-models/hosted-models>.

Check the menu at the left.

If you can’t use such models, you can use my API access to gpt.uio.no

<!-- deployment name: dscdays-oi-gpt-4o -->

Check the etherpad.

Consider adding these options:

    --context_window 160000 --max_tokens 1000 --max_output 10000

Now repeat the tasks we have done so far.

<!-- 
You can modify the max_tokens and context_window (in tokens) of locally running models.
&#10;For local mode, smaller context windows will use less RAM, so we recommend trying a much shorter window (~1000) if it's failing / if it's slow. Make sure max_tokens is less than context_window.
&#10;interpreter --local --max_tokens 1000 --context_window 3000
&#10; -->

## Let’s get some data

We will be using

- <https://datahub.io/core/population>
- <https://datahub.io/core/gdp>

## Tasks: population

> Download and inspect the csv file from
> https://github.com/datasets/population/blob/main/data/population.csv

> Plot the population size of Norway for all years present in the
> dataset

> Plot the population size of the Nordic countries for all years present
> in the dataset together in one plot

## Tasks: GDP, and combining datasets

> Plot the GDP of the Nordic countries together in one plot for all
> years present in the dataset from
> https://github.com/datasets/gdp/blob/main/data/gdp.csv

> Create a new csv file combining population size and gdp for Norway,
> use these files

- https://github.com/datasets/gdp/blob/main/data/gdp.csv
- https://github.com/datasets/population/blob/main/data/population.csv

## Optional: create a script file

> Write the final program to a script file

## Try on your own data

- Use excel files, or csv files, or …
- Need a datafile? Try Kaggle:
  <https://www.kaggle.com/datasets?sort=votes&fileType=csv>

## Computer use - Mac users

> Send an email to name@domain.no with subject “Some subject” and body
> “Body text”

<div class="fragment">

> Put my computer in dark mode

</div>

<div class="fragment">

> What is on my calendar today?

</div>

<div class="fragment">

> Add to my calendar: tomorrow from 10:00 - 11:00, Call Dr. John Doe for
> a meeting

</div>

## Other useful commands

Restart a previous conversation

``` .bash
interpreter --conversations
```

At the end of a session, before closing:

``` .bash
%jupyter
```

Save current conversation as a Jupyter notebook.

## Why use Open Interpreter?

- Sensitive data
- Offline with local models

## Ethical considerations

<div class="incremental">

- Where does the code come from?
- Who pays for this?
- Environmental footprint?

</div>
