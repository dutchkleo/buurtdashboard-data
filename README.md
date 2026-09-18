## What this is

`buurtdashboard-data` is a versioned data repository for the Dutch Buurtdashboard: a neighborhood-level climate adaptation dashboard. It provides neighborhood and municipality datasets, geographic boundaries, province geometry, indicator metadata, and an Excel download for use by dashboard applications and data analysts.

### Stack

- **Data formats:** JSON, CSV, XLSX
- **Geospatial format:** TopoJSON
- **Languages:** Dutch and English metadata
- **Runtime / framework:** None; this repository contains static data assets
- **Primary domains:** Climate effects, area characteristics, and social vulnerability

## How it's organized

```text
.
├── BuurtenDataset20240806_xaaaa.json
├── BuurtenDataset20240806_xaaab.json
├── BuurtenDataset20240806_xaaac.json
│   └── Neighborhood datasets from the August 2024 release, split across files
├── BuurtenDataset20240913_xaaaa.json
├── BuurtenDataset20240913_xaaab.json
├── BuurtenDataset20240913_xaaac.json
│   └── Neighborhood datasets from the September 2024 release, split across files
├── GemeenteDatasetTest20231011 (1).json
│   └── Municipality dataset test export
├── GemeenteGrenzen2023.json
├── GemeenteGrenzen2023-small.json
│   └── Full-size and reduced municipality boundary TopoJSON files
├── provinces.json
│   └── Province boundary TopoJSON
├── metadata.csv
│   └── Dutch indicator definitions and dashboard display metadata
├── metadata-english.csv
│   └── English indicator definitions and dashboard display metadata
└── BuurtdashboardDataDownload20240913.xlsx
    └── Spreadsheet export of the dashboard data
```

**How it fits together:** The `BuurtenDataset...json` files contain neighborhood-level indicator values, while the municipality and province files provide geographic boundaries for map visualizations. `metadata.csv` and `metadata-english.csv` describe the available indicators, their field names, units, categories, explanatory text, sources, and visualization settings. Dashboard consumers can combine the indicator fields with the corresponding geographic files and metadata to render neighborhood-level climate adaptation information.

The metadata covers indicators such as water depth during heavy rainfall, perceived temperature, groundwater levels, pile-rot and settlement risks, shade, green and blue space, population density, property value, housing, and social vulnerability.

## How to run it

This repository has no application runtime, build system, package manager, or test suite. It can be used directly as a static data source.

Clone the repository:

```bash
git clone https://github.com/Climate-Adaptation-Services/buurtdashboard-data.git
cd buurtdashboard-data
```

Inspect the available files:

```bash
ls -lh
```

Read the metadata:

```bash
head -n 5 metadata.csv
head -n 5 metadata-english.csv
```

Parse a JSON dataset with Python:

```bash
python -m json.tool BuurtenDataset20240913_xaaaa.json > /tmp/buurten-dataset.json
```

The JSON files are static exports and do not require environment variables or secrets. The three files for each `BuurtenDataset` release should be treated as parts of the same dataset. Use the matching metadata file to interpret indicator names and the relevant boundary files for map rendering.

## Try asking

- Which fields in `metadata-english.csv` describe heat vulnerability indicators?
- How are the September 2024 neighborhood dataset files split across `xaaаa`, `xaaab`, and `xaaac`?
- What is the difference between `GemeenteGrenzen2023.json` and `GemeenteGrenzen2023-small.json`?
