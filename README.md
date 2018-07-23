# Lutris Flatpak

An attempt at getting Lutris to run as a [Flatpak](https://flatpak.org/).

## Build

To compile Lutris as a Flatpak, you'll need both [Flatpak](https://flatpak.org/) and [Flatpak Builder](http://docs.flatpak.org/en/latest/flatpak-builder.html) installed. Once you manage that, do the following...

1. Add the platform dependencies...
  ```
  flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
  flatpak install --user flathub org.gnome.Sdk//3.28
  flatpak install --user flathub org.gnome.Platform//3.28
  ```

2. Compile and install the Flatpak...
  ```
  flatpak-builder --user --repo=lutris --force-clean build-dir org.lutris.Lutris.json
  flatpak remote-add --user lutris lutris --no-gpg-verify
  flatpak install --user lutris org.lutris.Lutris
  ```

3. Run it...
  ```
  flatpak run org.lutris.Lutris
  ```

## Development

The Python packages are built with https://github.com/flatpak/flatpak-builder-tools/tree/master/pip