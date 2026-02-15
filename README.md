mix-power-completion
====================

Fast bash completion for Elixir's [mix](https://hexdocs.pm/mix/) build tool with per-project caching.

## Features

- **Per-project caching** — each project gets its own task cache in `~/.mix_tasks/`
- **Auto-invalidation** — cache refreshes automatically when `mix.lock` changes
- **Lazy** — cache is created on first TAB press, no setup needed
- **Graceful fallback** — works outside mix projects (uncached)

## Install

### Manual

Clone and source the script:

    git clone git@github.com:davidhq/mix-power-completion.git
    cd mix-power-completion
    sudo cp mix /etc/bash_completion.d/
    source /etc/bash_completion.d/mix

Or install locally — add to `~/.bashrc`:

    source /path/to/mix-power-completion/mix

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
