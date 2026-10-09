# fuzzy-potato

Personal Gentoo overlay: ebuilds that are not in the main tree, newer (or
older) versions of existing packages, live `-9999` ebuilds and a few binary
packages.

No guarantees: these ebuilds are meant for personal use and may be untested,
outdated or broken.

## Installation

With `eselect repository` (package `app-eselect/eselect-repository`):

```sh
eselect repository add fuzzy-potato git https://github.com/0xlferra/fuzzy-potato.git
emaint sync -r fuzzy-potato
```

Or manually, by creating `/etc/portage/repos.conf/fuzzy-potato.conf`:

```ini
[fuzzy-potato]
location = /var/db/repos/fuzzy-potato
sync-type = git
sync-uri = https://github.com/0xlferra/fuzzy-potato.git
auto-sync = yes
```

and then running `emaint sync -r fuzzy-potato`.

## Usage

To install a package from the overlay:

```sh
emerge -av category/package::fuzzy-potato
```

Many ebuilds are keyworded `~amd64` (or have no keywords at all, like the
`-9999` ones), so you may need to add them to
`/etc/portage/package.accept_keywords`, for example:

```
net-misc/sunshine::fuzzy-potato **
```

## Packages

| Category | Packages |
|---|---|
| app-crypt | xsum |
| app-editors | scite |
| app-emulation | docker, x48ng |
| app-misc | broot, logiops, worker |
| app-portage | gcc-switcher |
| app-text | calibre, koodo-reader-bin |
| dev-java | icedtea-bin, openweb-start-bin, portecle |
| dev-lang | lazarus, powershell-bin |
| dev-libs | openssl, pkcs11-helper, rocm-comgr, rocm-device-libs, rocm-opencl-runtime, rocr-runtime, roct-thunk-interface |
| dev-tcltk | tcllib |
| dev-util | heroku, intel-ocl-sdk, mesa_clc |
| games-board | stockfish |
| games-emulation | emulationstation, sdlmame |
| games-fps | crispy-doom, ezquake, quake2-data |
| games-misc | fortune-mod-starwars |
| games-strategy | augustus |
| games-util | steamtinkerlaunch |
| gui-apps | quickshell |
| hypr-dotfiles | illogical-impulse |
| kde-misc | wallpaper-engine-kde-plugin |
| media-fonts | croscorefonts |
| media-gfx | mandelbulber |
| media-libs | libmysofa, mesa, oidn |
| media-plugins | gst-plugins-vaapi |
| media-sound | alsa-scarlett-gui, easyeffects |
| net-fs | nfs-utils, samba |
| net-im | discord |
| net-misc | icaclient, sunshine |
| sys-auth | fprintd-clients, open-fprintd, python-validity |
| sys-boot | mokutil |
| sys-fs | avfs, gcsfuse |
| virtual | jdk, jre |
| x11-terms | tabby-bin |

Available versions can be listed with `equery list -po '*::fuzzy-potato'`
(from `app-portage/gentoolkit`) or by browsing the overlay directories.

## Eclasses

The overlay ships a few eclasses used by its own ebuilds (`eclass/`), including
`dotnet`, `nuget`, `mono-env`, `libretro`, `libretro-core`, `golang-base-r1`,
`font-r1` and others.

## Issues

Bug reports and suggestions: <https://github.com/0xlferra/fuzzy-potato/issues>
