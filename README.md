# MoreThanDotfiles

[![Build Status][action-badge]][action-link]
[![Galaxy Role][role-badge]][galaxy-link]
[![MIT licensed][mit-badge]][mit-link]

This Ansible role is used to setup a minimal development environment supporting
various languages. For a full feature set of please visit the [dotfiles repo][dotfiles-repo].

Please fork and make it your own. Use this as inspiration.
![MoreThanDotfiles][demo]
![MoreThanDotfiles][speed-evidence]

List of tools being used:

- zsh

  - sheldon (plugin manager)
  - fastnodemanager
  - spaceship prompt
  - pyenv
  - fast (response time is 114ms)
  - vim like keybindings (search history j/k)
  - accept suggestions (<C-Y>)

- neovim

  - built-in lsp
  - completion support (lua, js, C, rust, yaml, ansible)
  - clipboard support over SSH
  - use Alt+[jkhl] to navigate between splits or tmux panes

- tmux

  - nvim aware, able to navigate between panes and vim splits seamlessly

Feel free to test drive end result using docker:

```sh
docker run -it --rm hurricane/morethandotfiles
```

## Requirements

None

## Role Variables

A description of the settable variables for this role are listed below,
including any variables that are in [defaults/main.yml](defaults/main.yml),
[vars/main.yml](vars/main.yml), and any variables that can/should be set via
parameters to the role.

```yaml
dotfiles_user: "{{ ansible_user | default(lookup('env', 'USER')) }}"
```

The user for whom [hurricanehrndz's dotfiles][dotfiles-repo] and all its
dependencies will get installed for, default is `ansible_user`.

```yaml
dotfiles_root: ""
```

Target directory for cloned Dotfiles repository, defaults to `$HOME/.dotfiles`.

```yaml
dotfiles_symlinks:
  - src: config/zshrc
    dst: .zhrc
```

Hash list of source and destination suffixes for symlinks to be created. Prefix
for source is `dotfiles_root` and prefix for destination is `$HOME`.

## Dependencies

- [hurricanehrndz.nvim_config][nvim_config-link]
- [hurricanehrndz.nerdfonts][nerdfonts-link]

## Example Playbook

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  vars:
    dotfiles_user: hurricanehrndz
  tasks:
    - name: Install morethandotfiles for hurricanehrndz
      include_role:
        name: hurricanehrndz.morethandotfiles
```

## License

[MIT][mit-link]

## Author Information

Carlos Hernandez | [e-mail](mailto:hurricanehrndz@techbyte.ca)

[role-badge]: https://img.shields.io/ansible/role/d/45889?style=for-the-badge
[galaxy-link]: https://galaxy.ansible.com/hurricanehrndz/morethandotfiles/
[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge
[mit-link]: https://raw.githubusercontent.com/hurricanehrndz/ansible-morethandotfiles/master/LICENSE
[dotfiles-repo]: https://github.com/hurricanehrndz/dotfiles
[nvim_config-link]: https://galaxy.ansible.com/hurricanehrndz/nvim_config
[nerdfonts-link]: https://galaxy.ansible.com/hurricanehrndz/nerdfonts
[action-badge]: https://img.shields.io/github/workflow/status/hurricanehrndz/ansible-morethandotfiles/CI?style=for-the-badge
[action-link]: https://github.com/hurricanehrndz/ansible-morethandotfiles/actions?query=workflow%3ACI
[demo]: ./images/morethandotfiles.gif
[speed-evidence]: ./images/benchmark.png
