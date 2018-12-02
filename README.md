i3-layout-loader
=========
[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)][license]

Layout loader with hooks for [i3wm]

## Installation

#### Requirements
* [i3wm] - A better tiling and dynamic window manager

### Guide
Clone this repository: `git clone https://github.com/hastinbe/i3-layout-loader.git ~/i3-layout-loader`

Edit the following example and append it to your `~/.config/i3/config`:

```
# Layout loader
exec --no-startup-id ~/i3-layout-loader/loader
```
Reload i3 configuration by pressing `mod+Shift+r`

#### Layouts

Layouts are generated with the `i3-save-tree` command and its output can be redirected to a file.
The file should be named according to its workspace name, so workspace "1" would be either "1.json" or just "1". For example:

```
i3-save-tree --workspace=1 > 1.json
i3-save-tree --workspace=name > name.json
```

If no layout path is specified with the `-d` option, `i3-layout-loader` will look in the following locations, in order:

```
./layouts
~/.config/i3/layouts
$XDG_CONFIG_HOME/i3/layouts
$XDG_CONFIG_DIRS/i3/layouts
```

For more information on saving layouts, refer to the [documentation](https://i3wm.org/docs/layout-saving.html).

#### Hooks

Hooks are stored in the `hooks` subdirectory of this script. To enable a hook, put a file in the `hooks` subdirectory that is
named according to the hooks below, and make it executable. The following hooks are available:

Filename | Description
-------- | -----------
pre-layout-load | Called before loading layouts
post-layout-load | Called after loading layouts
pre-layout-{workspace}-load | Called before loading an individual workspace layout
post-layout-{workspace}-load | Called after loading an individual workspace layout

Where `{workspace}` is substituted with name of the workspace you wish to create workspace specific hooks for.

## License

`i3-layout-loader` is released under [GNU General Public License v2][license]

Copyright (C) 1989, 1991 Free Software Foundation, Inc.

[i3wm]: https://i3wm.org
[license]: https://www.gnu.org/licenses/gpl-2.0.en.html
