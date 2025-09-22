# Ansible Role: Satty

[![CI](https://github.com/pluggero/ansible-role-satty/actions/workflows/ci.yml/badge.svg)](https://github.com/pluggero/ansible-role-satty/actions/workflows/ci.yml) [![Ansible Galaxy downloads](https://img.shields.io/ansible/role/d/pluggero/satty?label=Galaxy%20downloads&logo=ansible&color=%23096598)](https://galaxy.ansible.com/ui/standalone/roles/pluggero/satty)

An Ansible Role that installs a basic configuration of Satty.

The screenshot command could be used like this:

```bash
wayfreeze --after-freeze-cmd 'grim -g "$(slurp -d)" - | satty -f -'
```

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
satty_version: "x.x"
```

The version of satty to install can be defined in the variable `satty_version`.

```yaml
satty_install_method: "dynamic"
```

The method used to install satty can be defined in the variable `satty_install_method`.
The following methods are available:

- `source`: Installs satty from source
- `package`: Installs satty from the package manager of the distribution
  - **NOTE**: This method installs the latest version available in the package manager and not the version defined in `satty_version`.
- `dynamic`: Installs satty from package manager if available in the correct version, otherwise installs from source

```yaml
satty_force_install: false
```

Force reinstallation even if satty is already installed.

```yaml
satty_config_dir: "{{ ansible_env.HOME }}/.config/satty"
```

Directory where satty configuration is stored.

```yaml
satty_initial_tool: "rectangle"
```

Default tool selected when satty starts (rectangle, arrow, text, etc.).

```yaml
satty_copy_command: "wl-copy"
```

Command used for clipboard operations.

```yaml
satty_output_filename: "/tmp/test-%Y-%m-%d_%H:%M:%S.png"
```

Filename pattern for saved screenshots.

```yaml
satty_actions_on_enter: ["save-to-clipboard"]
satty_actions_on_escape: ["exit"]
```

Actions performed when Enter or Escape keys are pressed.

```yaml
satty_color_palette:
  - "#a52a2a"
  - "#1231e3"
  - "#6515cf"
  - "#ff1493"
  - "#ffd700"
  - "#008000"
```

Available colors for annotations and drawing tools.

```yaml
satty_font_family: "Roboto"
```

Font family used for text annotations.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - pluggero.satty
```

## License

MIT / BSD

## Author Information

This role was created in 2025 by Robin Plugge.
