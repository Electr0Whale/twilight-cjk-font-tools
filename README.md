# TWiLight Menu++ CJK Font Tools

[简体中文](README.zh-CN.md)

Python tools for rendering CJK fonts into pixel-aligned BMP tilesets that can
be imported into TWiLight Menu++ NFTR fonts with a compatible NFTR editor.
These scripts generate bitmap source images; they do not create or rewrite
NFTR files directly.

![TWiLight Menu++ font comparison](comparison.jpg)

> [!IMPORTANT]
> The Python scripts were developed with Gemini assistance. Review the output
> visually before importing it into a font.

## Requirements

- Python 3 with Pillow.
- `small.nftr` or `large.nftr` from
  `sd:/_nds/TWiLightMenu/extras/fonts/Default/`.
- A JSON character map exported by an NFTR editor.
- An NFTR editor capable of importing bitmap tiles.

Install Pillow:

```powershell
python -m pip install Pillow
```

## Included scripts

| Script | Purpose |
| --- | --- |
| `PixelBitmap_Base.py` | Basic single-font BMP tileset renderer with fixed offsets |
| `PixelBitmap_AutoCenter.py` | Automatically centers non-CJK characters inside each cell |
| `PixelBitmap_DualFallback.py` | Uses a secondary font when the primary font lacks a glyph and supports separate offsets |
| `PixelBitmap_ColorFix.py` | Normalizes bitmap colors to remove antialiasing or color-fringe artifacts before import |

The scripts open file-selection dialogs for the character-map JSON, source
font, optional fallback font, and output BMP.

## Workflow

1. Export the character order from the target NFTR as JSON.
2. Run the script that matches the desired fallback and alignment behavior.
3. Inspect the generated BMP at native resolution.
4. Import the BMP tiles into the original NFTR with an NFTR editor.
5. Save the NFTR under
   `sd:/_nds/TWiLightMenu/extras/fonts/<FontName>/` and test it on hardware.

The default layouts used by the scripts are `12 × 16` for small glyph cells
and `14 × 17` for large cells. Confirm cell size, font size, and offsets before
generating a complete tileset.

## Fonts and releases

The repository includes BDF material derived from WenQuanYi Bitmap Song and
Fusion Pixel Font. Their original licenses continue to apply. Existing
Releases provide WenQuanYi-only and WenQuanYi/Fusion combined builds.
