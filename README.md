[![Download dInk](https://img.shields.io/github/v/release/din0o0o/dink?label=Download&color=ffeb3b&labelColor=2d2d2d&style=for-the-badge)](https://github.com/din0o0o/dink/releases/latest)

# dInk

Font ink usage comparator: renders the same text in every installed font and ranks them by dark pixels.

## File structure

```
src/
├── main.py        # GUI, threading
├── engine.py      # Parsing fonts, rendering, counting dark pixels
├── settings.py    # Configuration, set before compiling
├── sample.txt     # Text for rendering
└── fonts.txt      # List of >300 fonts
```

## Build

```bash
pyinstaller dInk.spec
```

## Configuration

`settings.py`:
```
DPI = 300                           # render resolution
FONT_SIZE = 12                      # point size for all fonts
DARKNESS_THRESHOLD = 200            # greyscale cutoff 0-255
BASELINE_FONT = "Arial"             # reference font for relative %
FONTS_DIR = r"C:\Windows\Fonts"     # system fonts directory
LINE_SPACING_FACTOR = 1.15          # line height multiplier
```

## Procedure

1. Reads the font directory and matches it against `fonts.txt`.
2. Renders `sample.txt` to a greyscale image per font, using Pillow.
3. Counts dark pixels via histogram.
4. Writes `results.json` and `results.docx`.
