# dsh-session-search-plus

Two practical fixes for the experimental cross-session search in DeepSeek Harness 0.2.2-rc.2.

## What it changes

1. **Multi-word queries work.** `CBETA 敦煌` now matches an event that contains both words, instead of requiring them to be adjacent. Quoted text (`"exact phrase"`) still behaves as a phrase.
2. **Event reads are compact.** `session_event_read` omits `stream`, `usage` and `replayState` by default (about 18k -> 2.6k characters in a measured case). Pass `full: true` to get the raw event.

## Install

This bundle replaces the official experimental session-search bundle, so disable or remove
`@deepseek-ai/dsh-experimental-session-search` first (both register the same tool names).

```sh
dsh plugin --profile <your-profile> add github:zhengyuantai/dsh-session-search-plus
```

Restart DSH afterwards.

## Status

- Built on dsh 0.2.2-rc.2 (MIT).
- The query and compact-read changes are also described in
  [discussion #13215](https://github.com/deepseek-ai/deepseek-harness/discussions/13215).
- This is an early community bundle. Back up your profile before installing, and remove it with
  `dsh plugin --profile <your-profile> remove dsh-session-search-plus` if anything goes wrong.

## License

MIT. `lib/engine.js` and `lib/tools.js` are derived from the DeepSeek Harness packages
`@deepseek-ai/dsh-session-query-sqlite` and `@deepseek-ai/dsh-tool-session-query`.
