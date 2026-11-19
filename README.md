# GTK 4 configuration

Separate GTK 4 settings and CSS for compatible applications.

**[Documentation](https://aco-docs.readthedocs.io/en/latest/gtk4/)** ·
[Guide](https://aco-docs.readthedocs.io/en/latest/gtk4/guide/) ·
[Design & dependencies](https://aco-docs.readthedocs.io/en/latest/gtk4/design/) ·
[Installation and updates](https://aco-arch-dotfiles.readthedocs.io/en/latest/arch-package/)

```bash
curl -fsSL https://raw.githubusercontent.com/Akademie-Olympia/aco-arch-dotfiles/main/install.sh | bash -s -- gtk-4.0
```

Package: `aco-arch-dotfiles-gtk-4.0`. This standalone repository holds the development sources and the package recipe in
`packaging/arch/PKGBUILD`. The documentation of this component lives in the shared
[aco-docs](https://github.com/Akademie-Olympia/aco-docs) repository (one Read the Docs project for all small components).
Push to `main`; after a successful registry build update with `sudo pacman -Syu`. Details and local builds: [PACKAGING.md](PACKAGING.md).

### Customisation

`settings.ini` and `gtk.css` apply to GTK 4. Applications may bring their own themes; not every application honours all CSS rules. Check changes after an application restart.

Your own changes in the activated user copy survive synchronisation; new differing defaults appear as `.pacnew`.
See [update and recovery](https://aco-arch-dotfiles.readthedocs.io/en/latest/verification/).

[![Package safety](https://github.com/Akademie-Olympia/aco-gtk4/actions/workflows/package.yml/badge.svg)](https://github.com/Akademie-Olympia/aco-gtk4/actions/workflows/package.yml)

[MIT licence](LICENSE).
