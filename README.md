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
app-misc/logiops::fuzzy-potato **
```

## Packages

| Category | Packages |
|---|---|
| app-crypt | xsum |
| app-editors | scite |
| app-emulation | x48ng |
| app-misc | logiops, worker |
| app-portage | gcc-switcher |
| app-text | calibre, koodo-reader-bin |
| dev-java | icedtea-bin, openweb-start-bin, portecle |
| dev-lang | lazarus |
| games-emulation | emulationstation, sdlmame |
| games-fps | ezquake |
| games-misc | fortune-mod-starwars |
| games-strategy | augustus |
| games-util | steamtinkerlaunch |
| gui-apps | quickshell |
| hypr-dotfiles | illogical-impulse |
| kde-misc | wallpaper-engine-kde-plugin |
| media-sound | easyeffects |
| sys-auth | fprintd-clients, open-fprintd, python-validity |
| x11-terms | tabby-bin |

Available versions can be listed with `equery list -po '*::fuzzy-potato'`
(from `app-portage/gentoolkit`) or by browsing the overlay directories.

## Issues

Bug reports and suggestions: <https://github.com/0xlferra/fuzzy-potato/issues>
