# Climate Data Course - 2025 Updates

## Overview

This repository has been updated (November 2025) with enhanced scientific rigor, modern data access tools, and a new climate attribution module.

## What's New

### Updated Notebooks (Legacy versions preserved)

All original notebooks remain available. Updated versions have `_updated` suffix:

1. **1.Data_manipulation_and_vis_updated.ipynb**
   - Enhanced data validation and unit conversion
   - Improved error handling
   - Better cartographic visualizations
   - Physical plausibility checks

2. **2.Timeseries_and_2D_visualization_updated.ipynb**
   - Statistical significance testing (p-values, confidence intervals)
   - Comprehensive trend diagnostics (R², residuals, Q-Q plots)
   - Autocorrelation analysis
   - Multiple smoothing windows with WMO standards
   - Enhanced map projections

3. **3.Climate_data_store_updated.ipynb** ⭐ MAJOR UPDATE
   - Migration from `cdsapi` to `ecmwf-datastores-client`
   - Collection exploration and metadata inspection
   - Async vs sync data retrieval patterns
   - Job management and tracking
   - Result inspection before download
   - Robust error handling
   - ESGF and OPeNDAP sections retained

4. **4.Climatologies_and_anomalies_updated.ipynb**
   - WMO standard baseline periods (1961-1990, 1991-2020)
   - Statistical significance testing for anomalies
   - Uncertainty quantification with confidence intervals
   - Physical plausibility validation
   - Seasonal aggregation methodology verified

5. **5.Future_climate_updated.ipynb**
   - CMIP6 SSP scenarios explained with IPCC context
   - Ensemble statistics (multi-model mean and spread)
   - Model evaluation metrics (RMSE, bias, correlation)
   - Uncertainty quantification
   - IPCC AR6 WG1 findings integrated
   - Paris Agreement targets visualization

6. **6.Climate_attribution_statistics.ipynb** 🆕 NEW
   - Event attribution methodology (WWA approach)
   - Extreme value theory (GEV distributions)
   - Return period calculations
   - Case Study 1: Central Europe floods (Sept 2024)
   - Case Study 2: Mediterranean heatwaves
   - Physical mechanisms (Clausius-Clapeyron, atmospheric dynamics)
   - Bootstrap confidence intervals

## Technical Improvements

### Dependencies Updated

```python
# New packages added to requirements.txt
ecmwf-datastores-client  # Modern ECMWF data access
scikit-learn             # Machine learning tools
statsmodels              # Advanced statistics
```

Legacy `cdsapi` retained for backward compatibility.

### Scientific Enhancements

- **Statistical rigor**: All trends tested for significance
- **Uncertainty quantification**: Confidence intervals throughout
- **Physical validation**: Data plausibility checks
- **WMO standards**: Climatology periods follow international standards
- **IPCC alignment**: AR6 findings and methodology
- **Best practices**: Error handling, documentation, reproducibility

## Key Features

### Modern Data Access (Notebook 3)

```python
from ecmwf.datastores import Client

# New unified client
client = Client()

# Explore collections
collections = client.get_collections()

# Async retrieval with job tracking
remote = client.submit(collection_id, request)
remote.download('output.nc')
```

### Climate Attribution (Notebook 6)

```python
# Event attribution metrics
Probability Ratio (PR): How much more likely?
Intensity Change (ΔI): How much stronger?
Fraction Attributable Risk (FAR): Percentage due to climate change

# Example: Central Europe Floods 2024
PR ≈ 2.0  (doubled likelihood)
ΔI ≈ 20%  (intensity increase)
FAR ≈ 50% (half the risk attributable to climate change)
```

### Statistical Testing (Notebook 2)

```python
from scipy import stats

# Trend analysis with significance
slope, intercept, r_value, p_value, std_err = stats.linregress(x, y)

# Result: p < 0.001 (highly significant warming trend)
# Warming rate: ~0.18-0.20°C/decade
```

## Scientific References

- **IPCC AR6 WG1** (2021): Climate Change 2021: The Physical Science Basis
- **World Weather Attribution**: Rapid attribution studies
- **WMO Technical Regulations**: Climate normals (1991-2020)
- **CMIP6**: Eyring et al. (2016) Overview of CMIP6
- **Attribution methodology**: Stott et al. (2004, 2016)

## Learning Objectives

By completing these notebooks, students will:

1. ✅ Access climate data using modern ECMWF tools
2. ✅ Perform statistically rigorous trend analysis
3. ✅ Calculate climatologies following WMO standards
4. ✅ Evaluate climate model projections
5. ✅ Understand climate attribution methodology
6. ✅ Apply extreme value statistics
7. ✅ Quantify uncertainties in climate data
8. ✅ Validate results for physical plausibility

## Usage

### Setup

```bash
# Install dependencies
pip install -r requirements.txt

# Configure ECMWF credentials (for Notebook 3)
# Visit: https://cds.climate.copernicus.eu/
# Create account and get API key
```

### Running Notebooks

1. Start with setup notebooks in `set_up/`
2. Progress through notebooks 1-6 in order
3. Complete practice exercises (green boxes)
4. Refer to legacy versions for comparison

### Data Requirements

- **Sample data**: Included in `data/` directory
- **NASA GISTEMP**: Download link in Notebook 2
- **ERA5 data**: Retrieved via API in Notebook 3
- **CMIP6 data**: Access via ESGF or CDS (Notebook 5)

## Compatibility

- **Python**: 3.8+
- **Key packages**: xarray, cartopy, scipy, statsmodels
- **Data formats**: netCDF (CF-compliant)
- **Operating systems**: Linux, macOS, Windows

## Migration Guide: cdsapi → ecmwf-datastores-client

### Old (cdsapi)
```python
import cdsapi
c = cdsapi.Client()
c.retrieve('dataset-name', request, 'output.nc')
```

### New (ecmwf-datastores-client)
```python
from ecmwf.datastores import Client
client = Client()
client.retrieve('dataset-name', request, target='output.nc')
```

Benefits:
- Unified interface for CDS, ADS, and future stores
- Better job tracking and error handling
- Async operations for large downloads
- Result inspection before download

## Course Structure

```
notebooks/
├── set_up/                    # Initial setup
├── 1.Data_manipulation_*.ipynb      # XArray basics
├── 2.Timeseries_*.ipynb            # Statistical analysis
├── 3.Climate_data_store_*.ipynb    # Data access
├── 4.Climatologies_*.ipynb         # Baselines & anomalies
├── 5.Future_climate_*.ipynb        # CMIP6 projections
└── 6.Climate_attribution_*.ipynb   # Attribution science
```

## Case Studies

### Central Europe Floods (September 2024)
- 4-day heavy rainfall event
- Vb depression pattern
- Attribution: 2× more likely, 20% more intense
- Physical mechanism: Enhanced moisture transport

### Mediterranean Heatwaves
- Long-term warming trend (0.3°C/decade)
- Distribution shift in extremes
- Return period changes
- Future risk projections

## Contributing

When updating or extending these notebooks:

1. Maintain scientific accuracy
2. Test statistical significance
3. Quantify uncertainties
4. Validate against observations
5. Reference authoritative sources
6. Document assumptions
7. Include practice exercises

## License

This course material is provided for educational purposes. Data sources have their own licenses:
- **ERA5**: Copernicus License
- **CMIP6**: Various (check model documentation)
- **GISTEMP**: Public domain (NASA)

## Acknowledgments

- Original authors: Pedro Herrera Lormendez, Conrad Jackisch
- Data providers: ECMWF, NASA, CMIP6, ESGF
- Methodology: IPCC, World Weather Attribution
- 2025 updates: Enhanced with modern tools and attribution science

## Support

For questions or issues:
1. Check notebook markdown cells for explanations
2. Review practice exercise solutions (provided)
3. Consult scientific references
4. Validate calculations against known results

---

**Updated**: November 2025
**Course Level**: Intermediate to Advanced
**Prerequisites**: Basic Python, climate science fundamentals
**Estimated Time**: 15-20 hours (full course)
