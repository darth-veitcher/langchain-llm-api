# Langchain LLM API

A Langchain compatible implementation which enables the integration with [huggingface/textual-generation-inference](https://github.com/huggingface/text-generation-inference). Forked and customised from the original excellent [langchain-llm-api](https://github.com/1b5d/langchain-llm-api) companion library.

The main reason for implementing this package is to be able to use Langchain with any model run locally.

# Usage

You can install this as a python library using the command (until it's integrated with langchain itself)

```zsh
pip install langchain-llm-api
```

To use this langchain implementation with the `text-generation-inference`:

```py
from langchain_llm_api import LLMAPI

llm = LLMAPI(
    params={"temp": 0.2},
    verbose=True
)

llm("What is the capital of France?")
```

Or with streaming:

```py
from langchain_llm_api import LLMAPI, APIEmbeddings
from langchain.callbacks.streaming_stdout import StreamingStdOutCallbackHandler

llm = LLMAPI(
    params={"temp": 0.2},
    verbose=True,
    streaming=True,
    callback_manager=CallbackManager([StreamingStdOutCallbackHandler()])
)

llm("What is the capital of France?")
```

Optionally you can pass the `host_name`.

```py
llm = LLMAPI(
    host_name="http://myserver:8080",
    params={"temp": 0.2},
    verbose=True
)
```

## Embeddings

Not implemented yet. See [#199](https://github.com/huggingface/text-generation-inference/issues/199)
