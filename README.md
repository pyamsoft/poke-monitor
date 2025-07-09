# poke-monitor

Poke connected DP and HDMI displays after suspend

## What

On Linux, after suspend (sleep), some machines have trouble "waking up" a
connected DisplayPort or HDMI monitor.

This can be resolved by "poking" the monitor with something like xrandr to
"check" if the monitor is connected. This simple script iterates over all
connected monitors found by xrandr and "pokes" them by calling `--auto`
to see if a monitor will "wake up" after the system is resumed.

This is particularly useful on a system connected over SSH without an exported
xorg environment, as `poke-monitor` will first attempt to locate the active
Xauthority file on the system (searching standard locations).

This can assist SSH connected users when managing the display of remote
machines, for activities such as remote desktop or self-hosted
game streaming.

## How

All commands will attempt to locate the active Xauthority file,
and export a valid `DISPLAY` environment.

The `auto` command is the "default" action, which "pokes"
each found monitor by issuing an `xrandr --auto` command.

The `list` command simply calls `xrandr` on each connected monitor,
which usually will list all supported resolutions

The `reset` command will first attempt an `xrandr --off` on
each connected monitor, before "resetting" it with `xrandr --auto`.
This can be useful in multi-monitor environments which are
remotely connected over something like RDP, VNC, or Sunshine.

## Issues

Check the issues page on GitHub for any notes about outstanding or existing
issues. If you encounter a problem with `poke-monitor` of which no such
issue already exists please feel free to help the developer by creating an
issue ticket.

## License

GPLv2

```
  Copyright (C) 2025 pyamsoft

  This program is free software; you can redistribute it and/or
  modify it under the terms of the GNU General Public License
  as published by the Free Software Foundation; either version 2
  of the License, or (at your option) any later version.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU General Public License
  along with this program; if not, write to the Free Software Foundation, Inc.,
  51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

```
