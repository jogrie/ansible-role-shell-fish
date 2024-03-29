# Desktop fish role

Ansible role to install and configure fish shell. Intended to use on
a remote host for the users defined in fish_users.

## Requirements

None.

## Role Variables

None required.

### `fish_config`

List, that adds lines to `config.fish`.

``` yaml
fish_config:
  - set -x LC_ALL en_US.UTF-8
  - set -x LC_CTYPE en_US.UTF-8
```

### `fish_vi`

Enables `fish_vi_key_bindings` when `true`.

### `fish_aliases`

Add aliases with this variable.

``` yaml
fish_aliases:
  - name: v
    definition: vagrant
  - name: bv
    definition: bumpversion
```

### `fish_paths`

Add directories to `PATH`.

``` yaml
fish_paths:
    - "$HOME/bin"
    - "$HOME/.local/bin"
```

### `fish_functions`

Define fish functions:

``` yaml
fish_functions:
  - name: hh
    definition: |
      function hh --description 'Fuzzy find history'
        eval (history | fzf --no-color --no-sort --exact)
      end
```

### `fish_env`

Set environment variables:

``` yaml
shell_env:
  - name: EDITOR
    value: vi
```

### `fish_users`

Set users that get the fish config and functions

``` yaml
fish_users:
  - root
  - john
```

### `fish_default_shell`

Set fish as login shell for fish_users

``` yaml
fish_default_shell: true
```


## Dependencies

On Ubuntu it depends on `agoloncser.ubuntu_ppa`.

## Example Playbook

``` yaml
    - hosts: localhost
      vars:
      roles:
         - agoloncser.shell_fish
```

## License

BSD

## Author Information

[github.com/agoloncser](https://github.com/agoloncser)
