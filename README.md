mix-completion
==============

Fast bash completion for Elixir's [mix](https://hexdocs.pm/mix/) build tool with per-project caching.

## Features

- **Per-project caching** — each project gets its own task cache in `~/.mix_tasks/`
- **Auto-invalidation** — cache refreshes automatically when `mix.lock` changes
- **Lazy** — cache is created on first TAB press, no setup needed
- **Graceful fallback** — works outside mix projects (uncached)

## Install

### Manual

Clone and source the script:

    git clone git@github.com:sparkworx/mix-completion.git
    cd mix-completion
    sudo cp mix /etc/bash_completion.d/
    source /etc/bash_completion.d/mix

Or install locally — add to `~/.bashrc`:

    source /path/to/mix-completion/mix

### Homebrew

    brew tap homebrew/completions
    brew install mix-completion

## Usage

    $ mix <TAB>
      archive  archive.build  compile  deps  deps.clean  ...

    $ mix dep<TAB>
      deps  deps.clean  deps.compile  deps.get  deps.tree  deps.unlock  deps.update

The first TAB press in a project has a brief delay while the task list is built. Subsequent completions are instant.

## Cache management

Caches are stored in `~/.mix_tasks/`. To reset all caches:

    rm -rf ~/.mix_tasks/

Individual project caches are invalidated automatically when `mix.lock` changes (e.g. after `mix deps.get`).

## Acknowledgments

This project was originally created by [David Krmpotic](https://github.com/davidhq) as
[mix-power-completion](https://github.com/davidhq/mix-power-completion) — a bash completion
script for Elixir's mix with clever shortcut expansion and colored output. Thank you, David,
for the inspiration and the foundation this builds on.

This fork is a ground-up rewrite that narrows the scope to bash completion only, replacing
the global task cache and `m` shortcut wrapper with per-project caching and automatic
invalidation via `mix.lock` checksums. The original shortcut and color features have been
removed in favor of a smaller, faster script focused solely on TAB completion.

## License

Apache License 2.0 — see [LICENSE](LICENSE) for details.
