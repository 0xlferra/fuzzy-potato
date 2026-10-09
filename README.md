# fuzzy-potato

Overlay Gentoo personale: ebuild che non sono nel tree ufficiale, versioni più
recenti (o più vecchie) di pacchetti esistenti, live ebuild `-9999` e qualche
pacchetto binario.

Nessuna garanzia: gli ebuild sono pensati per uso personale e possono essere
non testati, obsoleti o rotti.

## Installazione

Con `eselect repository` (pacchetto `app-eselect/eselect-repository`):

```sh
eselect repository add fuzzy-potato git https://github.com/0xlferra/fuzzy-potato.git
emaint sync -r fuzzy-potato
```

Oppure a mano, creando `/etc/portage/repos.conf/fuzzy-potato.conf`:

```ini
[fuzzy-potato]
location = /var/db/repos/fuzzy-potato
sync-type = git
sync-uri = https://github.com/0xlferra/fuzzy-potato.git
auto-sync = yes
```

e poi `emaint sync -r fuzzy-potato`.

## Uso

Per installare un pacchetto dall'overlay:

```sh
emerge -av categoria/pacchetto::fuzzy-potato
```

Molti ebuild sono in `~amd64` (o senza keyword, come i `-9999`), quindi
potrebbe servire aggiungerli a `/etc/portage/package.accept_keywords`, ad esempio:

```
net-misc/sunshine::fuzzy-potato **
```

## Pacchetti

| Categoria | Pacchetti |
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

Le versioni disponibili si vedono con `equery list -po '*::fuzzy-potato'`
(da `app-portage/gentoolkit`) o direttamente nelle directory dell'overlay.

## Eclass

L'overlay include alcune eclass usate dai propri ebuild (`eclass/`), tra cui
`dotnet`, `nuget`, `mono-env`, `libretro`, `libretro-core`, `golang-base-r1`,
`font-r1` e altre.

## Segnalazioni

Problemi e suggerimenti: <https://github.com/0xlferra/fuzzy-potato/issues>
