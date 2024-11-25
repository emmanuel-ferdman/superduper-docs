# Getting started

![](https://www.youtube.com/watch?v=9rA0dGmK2-s)

## Installation

If you plan to install Superduper, you'll need at least:

- `python` 3.10+
- `pip` 22.0.4+

Superduper is available on [PyPi.org](https://pypi.org/project/superduper-framework/).

```bash
pip install superduper-framework
```

:::danger
**Note that Superduper is not installed with `pip install superduper`.**
There is another unrelated package occupying this namespace.
:::

This command will install `superduper` along with a minimal set of common dependencies required for running the framework.

Superduper also includes several plugins, which are all installable with a `superduper_` prefix. For 
example, to install the MongoDB bindings, do:

```bash
pip install superduper_mongodb
```

## Apply your first template

Note that Superduper allows developers to completely 
own their applications, self-hosting all models and data, if so wished. 
To view which templates are available, type:

```bash
superduper ls
```

To view a template do:

```bash
superduper inspect <template_name>
```

To install a template, do:

```bash
superduper bootstrap <template_name>
```

To try a simple RAG application either do:

```bash
export OPENAI_API_KEY=sk-...
superduper bootstrap simple_rag
superduper apply simple_rag --variables '{"table_name": "my-collection"}' --data_backend mongodb://localhost:27017/test_db
```

Or from python:

```python
from superduper import superduper
from superduper.templates import rag

db = superduper('mongodb://localhost:27017/test_db')
rag_app = rag(table_name='my-collection')
db.apply(rag_app)
```

Once this command has successfully executed, view the results in the user interface:

```bash
superduper start
```

Navigate to the execute tab to test the results:

![](/img/screenshot_execute.png)

Or execute queries from the command line:

```bash
superduper execute
```