# Queensland Drought Data Platform

Gridded **SPI**, **SPEI**, and a bioregion-aware **Protracted Drought Classification** for Queensland, Australia, covering **January 2000 &ndash; December 2025** at 0.05&deg; (~5km) resolution. Built as part of a PhD research project on explainable AI approaches for reducing basis risk in weather index insurance for agribusiness, University of Southern Queensland.

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-c9a227.svg)](https://creativecommons.org/licenses/by/4.0/)
[![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.21418371-3568a6.svg)](https://doi.org/10.5281/zenodo.21418371)
[![Paper](https://img.shields.io/badge/Paper-10.1016%2Fj.scitotenv.2026.181564-b4402f.svg)](https://doi.org/10.1016/j.scitotenv.2026.181564)

---

### 🔗 Quick links

| | |
|---|---|
| 🌐 **Project website** | [jspcharles.github.io/Drought_QLD](https://jspcharles.github.io/Drought_QLD/) |
| 🗺️ **Interactive map** (live, no login required) | [chafinans.users.earthengine.app/view/qld-drought-explorer](https://chafinans.users.earthengine.app/view/qld-drought-explorer) |
| 📦 **Full dataset** (Zenodo, CC BY 4.0) | [doi.org/10.5281/zenodo.21418371](https://doi.org/10.5281/zenodo.21418371) |
| 📄 **Methodology paper** | [doi.org/10.1016/j.scitotenv.2026.181564](https://doi.org/10.1016/j.scitotenv.2026.181564) |

> ℹ️ GitHub doesn't allow live, interactive embeds inside a README (iframes are stripped for security), so the map below is a static preview. For the real interactive version — switch indices/scales/months and download any layer on the spot — use the **project website** or **interactive map** links above.

---

### Example output

Monthly SPI-1 and Protracted Drought Classification, Cape York Peninsula, 2008 (the case study referenced in the methodology paper):

![SPI-1 and Protracted Drought, Queensland 2008](./QLD_protracted_drought_2008.png)

---

## What's in this dataset

| Product | Description | Scales |
|---|---|---|
| **SPI** | Standardized Precipitation Index | 1, 3, 6, 12 months |
| **SPEI** | Standardized Precipitation-Evapotranspiration Index | 1, 3, 6, 12 months |
| **Protracted Drought Classification** | Flags repeat drought events occurring before full bioregion-specific recovery | &mdash; |

All products are derived from [SILO](https://www.longpaddock.qld.gov.au/silo/) gridded climate data (Queensland Government, Department of Environment and Science), on a consistent 382 &times; 311 grid at 0.05&deg; resolution.

**Protracted drought definition:** a drought event (SPI-1 &le; -1.0) is flagged as *protracted* if it recurs before the bioregion has recovered (SPI-1 &ge; -0.5) for a sufficient period &mdash; recovery windows range from 2 months (Gulf Plains) to 5 months (Channel Country), following the methodology in Joseph et al. (2026), see [Citation](#citation) below.

## Repository structure

```
Drought_QLD/
├── docs/
│   └── index.html                        # Project landing page (GitHub Pages source)
├── PP_crop_to_qld.ipynb                   # Clip AU-wide grids to Queensland
├── PP_spi_calculation.ipynb               # SPI computation from SILO rainfall
├── PP_data_consolidate.ipynb              # Merge yearly files into consolidated NetCDFs
├── PP_protracted_drought_label.ipynb      # Protracted drought labelling (bioregion recovery lags)
├── PP_change_variable_name.ipynb          # Variable/naming standardisation
├── PP_netcdf_to_geotiff.ipynb             # NetCDF -> multi-band GeoTIFF for Earth Engine
├── 5. PP_combine_nc.ipynb                 # Final consolidation pass
├── QLD_protracted_drought_2008.png        # Example visualisation (shown above)
└── README.md
```

The processed `.nc` data files themselves are **not** stored in this repository (too large for Git) &mdash; they're archived on Zenodo, linked above.

## Citation

If you use this data or code, please cite both the dataset and the methodology paper:

**Dataset:**
> Joseph, C., Wang, Q.J., Mushtaq, S., Li, Y., Barratt, J., & Barratt, T. (2026). Queensland Drought Indices Dataset (SPI, SPEI, Protracted Drought Classification), 2000&ndash;2025 [Data set]. Zenodo. https://doi.org/10.5281/zenodo.21418371

**Methodology paper:**
> Joseph, C., Wang, Q.J., Mushtaq, S., Li, Y., Barratt, J., & Barratt, T. (2026). Deep learning the droughts: Spatiotemporal monitoring of protracted dry conditions in Queensland, Australia. *Science of the Total Environment*, 1021, 181564. https://doi.org/10.1016/j.scitotenv.2026.181564

**Underlying climate data:**
> Derived from SILO gridded climate data, © State of Queensland (Department of Environment and Science) 2000&ndash;2026, used under CC BY 4.0.

## License

This dataset and the code in this repository are released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) &mdash; free to share and adapt with attribution.

## Contact

**Charles Joseph** &middot; PhD Candidate, University of Southern Queensland
