# Monthly Total Suspended Solids (TSS) Analysis Over Kokkilai Lagoon Using Sentinel-2 & Xarray-EE
## Overview

This project analyzes Total Suspended Solids (TSS) dynamics within the Kokkilai Lagoon, located in the Northern Province of Sri Lanka. Coastal lagoons like Kokkilai play a critical role in biodiversity, fisheries, and hydrological regulation, but they are highly sensitive to sediment load, river inflows, monsoonal variations, and anthropogenic disturbances.

Monitoring TSS levels is important because increasing turbidity can indicate:
1. Declining water quality
2. Sediment inflow from rivers or catchments
3. Erosion or dredging activities
4. Ecological stress affecting fish, mangroves, and seagrass

Using Google Earth Engine (GEE) integrated with the xee / xarray-ee Python API, this workflow extracts cloud-filtered Sentinel-2 surface reflectance data, computes the TSS index, aggregates it monthly and weekly, and visualizes temporal trends.
This represents a scalable, reproducible approach for long-term lagoon water quality monitoring using open Earth observation data.


## Tools & Libraries
1. Google Earth Engine (Python API)
2. geemap – interactive ROI selection
3. xarray-ee / xee – load GEE ImageCollections directly into xarray
4. xarray / pandas – data transformation & aggregation
5. matplotlib – map rendering & time series visualization
6. NumPy / Pandas – analysis utilities

## Datasets Used
1. Sentinel-2 Surface Reflectance (S2_SR_HARMONIZED)
 - Bands used: B2 (Blue), B3 (Green), B5 (Red-edge), & B7 (SWIR)

2. Sentinel-2 Cloud Probability
 - Used for cloud masking (threshold: < 20%).

# Computed Indices
1. NDWI (Normalized Difference Water Index)
   Used to isolate water pixels:
   NDWI = (Green - NIR) / (Green + NIR)

2. TSS Proxy
   A reflectance-based TSS indicator derived from:
   TSS = B7 * (B5 / B2)

Higher values indicate:
1. Higher suspended sediment load
2. Higher turbidity
3. Possibly higher river input or disturbance

### Monthly TSS distribution across Kokkilai Lagoon for 2024, generated from cloud-masked Sentinel-2 imagery
<img width="1696" height="590" alt="image" src="https://github.com/user-attachments/assets/12b7e2b8-4296-4af7-a748-dc748977857c" />
The maps illustrate how Total Suspended Solids vary seasonally, from relatively low levels early in the year to significantly elevated concentrations during the southwest and northeast monsoon periods. The color scale (dark blue → light blue → green → yellow → red) corresponds to lower–higher TSS values respectively, highlighting strong spatial contrasts influenced by hydrological inputs, tidal mixing, and sediment inflows.

## Key Insights from the Visualization
1. January–February: Mostly low TSS (deep blues) indicating calm water, minimal inflow, and stable lagoon conditions.
2. March–June: Gradual increase in suspended sediments (greens and yellows). Likely influenced by pre-monsoon rainfall and catchment runoff.
3. July–October: Peak sediment load (extensive red zones). This period aligns with high rainfall and increased river discharge.
4. November–December: TSS levels decline as turbulence decreases, returning to moderate–low values.

These patterns align well with Sri Lanka’s monsoon cycles and lagoon hydrodynamics.

## Notes
- Cloud masking is strictly enforced (probability < 20%) to ensure high-quality TSS retrieval.
- NDWI > 0.1 ensures that only valid water pixels are analyzed, preventing false turbidity detection from land.
- TSS index used here is a proxy, not a field-calibrated turbidity measurement. However, it is effective for relative spatial/temporal turbidity analysis.
- Monthly aggregation uses median to suppress outliers and noisy pixels.

## Conclusion

This study provides a clear, reproducible workflow to monitor sediment-turbidity dynamics in Kokkilai Lagoon using cloud-masked Sentinel-2 imagery. The results reveal strong seasonal variation, with sediment concentration peaking during monsoonal months. This workflow can support:
- Water quality monitoring
- Lagoon ecosystem management
- Catchment sediment flow assessment
- Long-term environmental reporting


