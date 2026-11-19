# GTK4 configuration

Getrennte GTK4-Einstellungen und CSS für kompatible Anwendungen.

**[Dokumentation](https://aco-arch-dotfiles.readthedocs.io/en/latest/components/#gtk4)** ·
[Installation und Updates](https://aco-arch-dotfiles.readthedocs.io/en/latest/arch-package/)

```bash
curl -fsSL https://raw.githubusercontent.com/Akademie-Olympia/aco-arch-dotfiles/main/install.sh | bash -s -- gtk-4.0
```

Paket: `aco-arch-dotfiles-gtk-4.0`. Dateien: `~/.config/gtk-4.0/settings.ini` und `gtk.css`.
Quellen und `packaging/arch/PKGBUILD` werden hier gepflegt. Nach Push auf `main`
und erfolgreichem Registry-Build aktualisiert `sudo pacman -Syu` das Paket.
Entwicklung und Builds: [PACKAGING.md](PACKAGING.md).

### Anpassung

`settings.ini` und `gtk.css` gelten für GTK4. Anwendungen können eigene Themes verwenden; nicht jede Anwendung übernimmt alle CSS-Regeln. Änderungen nach einem Anwendungsneustart prüfen.

Eigene Änderungen in der aktivierten Benutzerkopie bleiben bei der Synchronisierung erhalten; neue abweichende Vorgaben erscheinen als `.pacnew`. Siehe [Update und Wiederherstellung](https://aco-arch-dotfiles.readthedocs.io/en/latest/verification/).

[![Package safety](https://github.com/Akademie-Olympia/aco-gtk4/actions/workflows/package.yml/badge.svg)](https://github.com/Akademie-Olympia/aco-gtk4/actions/workflows/package.yml)

[MIT-Lizenz](LICENSE).
