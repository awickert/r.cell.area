# r.cell.area

GRASS GIS addon that calculates the area of each raster cell within the
current computational region.

Works for any projected CRS (using the PROJ meters-per-map-unit conversion
factor, so metres, US survey feet, international feet, and all other linear
units are handled automatically) and for geographic (latitude/longitude) CRS
(using a spherical approximation based on cell latitude).

## Installation

```bash
g.extension r.cell.area
```

Or, to install from this repository:

```bash
g.extension r.cell.area url=https://github.com/awickert/r.cell.area
```

## Usage

```bash
# Square-metre cell areas in a projected location
r.cell.area output=cell_area units=m2

# Square-kilometre cell areas in a geographic location
r.cell.area output=cell_area units=km2
```

See `r.cell.area --help` or the [module manual](r.cell.area.md) for full
documentation.

## Supported output units

| Option | Unit |
|--------|------|
| `m2`   | square metres |
| `km2`  | square kilometres |

## Relationship to OSGeo/grass-addons

The canonical release of this module lives in
[OSGeo/grass-addons](https://github.com/OSGeo/grass-addons) under
`src/raster/r.cell.area/`. That repository uses a **squash-merge** convention,
so each PR lands as a single commit and the granular development history is
lost.

This repository exists to preserve the complete commit history — every
individual fix, refactor, and test addition — which serves as the full
provenance record and citation basis for the module. Development happens here
and is periodically contributed upstream to grass-addons as squash-merged PRs.

## Author

Andrew D. Wickert

## License

GPL v3 — see [LICENSE](LICENSE)
