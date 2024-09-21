# The Lounge

The Lounge is a modern web IRC client designed for self-hosting.

thelounge.chat

![thelounge logo](https://thelounge.chat/assets/logos/logo/TL_White&Yellow_Horizontal_logotype_Transparent_Bg/TL_White&Yellow_Horizontal_logotype_Transparent_Bg.svg)

## Overview

- **Modern features brought to IRC.** Push notifications, link previews, new message markers, and more bring IRC to the 21st century.
- **Always connected.** Remains connected to IRC servers while you are offline.
- **Cross platform.** It doesn't matter what OS you use, it just works wherever Node.js runs.
- **Responsive interface.** The client works smoothly on every desktop, smartphone and tablet.
- **Synchronized experience.** Always resume where you left off no matter what device.

## How to use this Makejail

```sh
mkdir -p .volumes/db
appjail makejail \
    -j thelounge \
    -f gh+AppJail-makejails/thelounge \
    -o virtualnet=":<random> default" \
    -o nat \
    -o expose=9000 \
    -o fstab="$PWD/.volumes/db thelounge-db <volumefs>"
appjail start thelounge
```

### Creating a new user

```sh
appjail cmd jexec thelounge -U thelounge thelounge add MyUser
```

### Arguments (stage: build):

* `thelounge_tag` (default: `13.4`): see [#tags](#tags).

### Check current status

The custom stage `thelounge_status` can be used to run `top(1)` to check the status of Miniflux.

```sh
appjail run -s thelounge_status thelounge
```

### Log

To view the log generated by the web application, run the custom stage `thelounge_log`.

```sh
appjail run -s thelounge_log thelounge
```

### Volumes

| Name           | Owner | Group | Perm | Type | Mountpoint |
| -------------- | ----- | ----- | ---- | ---- | ---------- |
| thelounge-db   | 1001  | 1001  |  -   |  -   | /app       |

## Tags

| Tag    | Arch    | Version        | Type   |
| ------ | ------- | -------------- | ------ |
| `13.4` | `amd64` | `13.4-RELEASE` | `thin` |
| `14.0` | `amd64` | `14.0-RELEASE` | `thin` |
