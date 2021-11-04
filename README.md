## Instrucciones de Optimización

Estas instrucciones deben realizarse en modo ROOT

#### [ Eliminar Gnome-Software de Fedora / CentOs ]

```sh

➡ $ systemctl status packagekit
➡ $ systemctl stop packagekit
➡ $ systemctl mask packagekit
➡ $ yum remove PackageKit*
➡ $ mv /usr/libexec/tracker-miner-fs-3 /usr/libexec/tracker-miner-fs-3-disable

```

#### [ Desabilitar el proceso de Evolution ]

```sh

$ mv /usr/lib64/evolution-data-server/ /usr/lib64/evolution-data-server-disable

```

#### [ Evitar que evolution se actualice (Modificar DNF o YUM)]

```sh

➡ $ nano /etc/dnf/dnf.conf 
➡ $ nano /etc/yum.conf

``` 

[ Agregar al archivo .conf ]

```sh

....
exclude=evolution*
...

```

#### [ Gnome tracker service disable ]

```sh

➡ $ echo "Hidden=true" >> /etc/xdg/autostart/tracker-extract.desktop
➡ $ echo "Hidden=true" >> /etc/xdg/autostart/tracker-miner-apps.desktop
➡ $ echo "Hidden=true" >> /etc/xdg/autostart/tracker-miner-fs.desktop
➡ $ echo "Hidden=true" >> /etc/xdg/autostart/tracker-miner-fs-3.desktop
➡ $ echo "Hidden=true" >> /etc/xdg/autostart/tracker-miner-rss-3.desktop
➡ $ echo "Hidden=true" >> /etc/xdg/autostart/tracker-miner-user-guides.desktop
➡ $ echo "Hidden=true" >> /etc/xdg/autostart/tracker-store.desktop

➡ $ dbus-launch --exit-with-session gsettings set org.freedesktop.Tracker.Miner.Files crawling-interval -2
➡ $ dbus-launch --exit-with-session gsettings set org.freedesktop.Tracker.Miner.Files enable-monitors false
➡ $ yes | LANG=C tracker reset --hard
➡ $ sed -i 's/X-GNOME-Autostart-enabled=.*/X-Gnome-Autostart-enabled=false/' /etc/xdg/autostart/tracker-store.desktop

```

#### [ Disable plymouth boot ]

```sh
➡ $ sudo dnf remove plymouth*

## Edit /etc/default/grub with nano and REMOVE "rhgb" from GRUB_CMDLINE_LINUX="rhgb quiet"
➡ $ sudo nano /etc/default/grub

## Edit /etc/default/grub
GRUB_CMDLINE_LINUX="rhgb quiet"
## to
GRUB_CMDLINE_LINUX="quiet"

## And rebuild GRUB
➡ $ sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg

```

#### [ Contacto ]

[ #Twitter ]
* https://www.twitter.com/arteaprogramar

[ #Facebook ]
* https://www.fb.com/arteaprogramar

[ #Instagram ]
* https://www.instagram.com/arteaprogramar

[ #GitHub ]
* https://www.github.com/arteaprogramar

[ #PlayStore Perfil ]
* https://play.google.com/store/apps/dev?id=8045357588448663731
