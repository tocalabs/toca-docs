# .toca/tocabot

This directory powers the [Toca Docs AI Search](../../src/common/documentation_ai.md) functionality.

- `default_sources.json`: This file specifies which docs are provided to the AI for **every query**, regardless of the user's context. It should include broadly relevant documents that are useful to provide context for most queries.

- `keyword_sources.json`: This file specifies which docs are provided to the AI based on the words in a user's query. It should include documents that are relevant to specific keywords or phrases that users might search for.

The format of these sources is the same `:docs-link[]` format we use throughout the docs (see [Linking to other docs](../../README.md#linking-to-other-docs)). This means you can include `Platform`, `Action`, `Connector`, `AppAction`, and `AppComponent` docs as sources.

> **Note:** In addition to these files, the AI also dynamically fetches docs based on their semantic similarity to the user's query. This means that even if a document is not explicitly listed in either `default_sources.json` or `keyword_sources.json`, it can still be included in the AI's response if it is contextually relevant.