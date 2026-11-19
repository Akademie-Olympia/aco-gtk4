# GTK 4 – moderne Anwendungen

GTK 4 (mit libadwaita) zeichnet neuere GNOME-Programme und viele Portal-Dialoge. Dieses Paket färbt sie in der Palette des Desktops.

## So greifen die Dateien ineinander

GTK liest beim Start einer Anwendung zwei Dateien:

- `settings.ini` – **Verhalten**: dunkles Thema bevorzugen, Symbolsatz, Schrift, Cursor, Animationen.
- `gtk.css` – **Aussehen**: überschreibt Farben und Rahmen des Themas mit der Catppuccin-Mocha-Palette.

Das Thema bleibt `Adwaita-dark`; `gtk.css` färbt es um. Dadurch bleiben Layout und Bedienelemente
vertraut, nur die Farben passen zum Rest des Desktops.

| Einstellung (`settings.ini`) | Wert | Wirkung |
| --- | --- | --- |
| `gtk-application-prefer-dark-theme` | `1` | Dunkle Variante bevorzugen |
| `gtk-theme-name` | `Adwaita-dark` | Grundthema |
| `gtk-icon-theme-name` | `Adwaita` | Symbole (`adwaita-icon-theme`) |
| `gtk-font-name` | JetBrainsMonoNL Nerd Font 10 | Schrift aller Dialoge und Menüs |
| `gtk-cursor-theme-name` / `-size` | Adwaita / 20 | Passt zu `XCURSOR_SIZE` in Hyprland |
| `gtk-enable-animations` | `0` | Keine Animationen – wirkt schneller |

## Der Unterschied zu GTK 3

GTK 4 und libadwaita nutzen **eigene benannte Farben** (`window_bg_color`, `headerbar_bg_color`, `accent_bg_color` …) und ignorieren
`gtk-theme-name` weitgehend. Deshalb ist `gtk.css` hier kurz: Sie definiert nur diese Farben neu und lässt das
Layout der Programme unangetastet.

| Farbe | Wert | Zweck |
| --- | --- | --- |
| `window_bg_color` | `#1e1e2e` | Fensterhintergrund |
| `view_bg_color` | `#181825` | Listen, Textfelder |
| `headerbar_bg_color` | `#181825` | Kopfleiste |
| `card_bg_color` | `#313244` | Karten, Gruppen |
| `popover_bg_color` | `#1e1e2e` | Menüs, Popups |
| `accent_bg_color` | `#89b4fa` | Hervorhebungen, Schalter |

Aktuelle Programme melden die Dunkelwahl auch über das Portal; Fenster, die trotzdem hell bleiben, kontrollierst du mit
`gsettings get org.gnome.desktop.interface color-scheme` (erwartet: `prefer-dark`).

## Eigene Anpassungen

```css
/* ~/.config/gtk-4.0/gtk.css */
@define-color accent_bg_color #cba6f7;   /* Mauve als Akzent */
@define-color accent_color #cba6f7;
```

Starte die Anwendung neu; zum Testen hilft `GTK_DEBUG=interactive <programm>`.

## Fehlersuche

- **Nichts ändert sich:** Läuft das Programm als Flatpak, sieht es `~/.config/gtk-4.0` nicht automatisch.
- **Zu wenig Kontrast:** `accent_fg_color` (Text auf Akzent) muss zur gewählten Akzentfarbe passen.
- **Ältere Programme:** [GTK 3](https://aco-gtk3.readthedocs.io/en/latest/).

## Farbpalette (Catppuccin Mocha)

Alle Komponenten nutzen dieselben Farben, damit Terminal, Launcher, Dateimanager und Dialoge zusammenpassen:

| Rolle | Farbe | Verwendung |
| --- | --- | --- |
| Hintergrund | `#1e1e2e` | Fenster, Terminal |
| Tiefer Hintergrund | `#181825` | Leisten, Listen, Seitenleisten |
| Fläche | `#313244` | Eingabefelder, Buttons, Auswahl |
| Text | `#cdd6f4` | Schrift |
| Akzent | `#89b4fa` | Fokus, Rahmen, Auswahl |
| Treffer | `#94e2d5` | Suchtreffer |

## Anpassen und zurücksetzen

`~/.config/gtk-4.0` ist ein Link auf deine bearbeitbare Kopie unter
`~/.local/share/arch-dotfiles/config/gtk-4.0/`. Dort kannst du alles ändern; `pacman -Syu` überschreibt
deine Änderungen **nicht**. Bringt ein Update neue Vorgaben mit, landen sie als `.pacnew`-Datei neben deiner
Version, und du übernimmst, was du willst (`aco sync` führt zusammen, `aco status` zeigt den Zustand).
Zurück zu den Vorgaben: `aco deactivate gtk-4.0` stellt die früheren Einstellungen wieder her,
`aco install gtk-4.0` aktiviert die Paketvorgaben erneut.
