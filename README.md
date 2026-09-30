# PNG to SVG

Convert every `.png` file in an input directory into an `.svg` file in an output
directory.

This preserves the original PNG colors and image quality by embedding each PNG
inside an SVG wrapper.

```bash
./png-to-svg/png-to-svg /path/to/input-pngs /path/to/output-svgs
```

Example:

```bash
./png-to-svg/png-to-svg ./input-images ./svg-output
```

## Optimize SVGs for web pages

The generated SVGs are self-contained, but base64-embedded PNG data makes the
SVG files larger than they need to be for web pages.

Use `optimize-svg-for-web` to create small SVG wrappers and move the PNG data
into cacheable image assets:

```bash
./png-to-svg/optimize-svg-for-web ./svg-output ./web-svg-output
```

This writes optimized SVG files plus PNG files in `./web-svg-output/assets`.
Use these SVGs inline in HTML or in an asset pipeline that keeps the `assets`
folder next to them.

If you need each SVG to remain a single self-contained file, use:

```bash
./png-to-svg/optimize-svg-for-web --inline ./svg-output ./web-svg-output
```
