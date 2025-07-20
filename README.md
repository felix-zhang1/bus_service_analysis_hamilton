# Hamilton City Bus Service Coverage Analysis

This project analyzes the public bus service coverage in Hamilton City using ArcGIS. It identifies areas that lack bus stop coverage and provides visual maps to help people—especially international students—better understand which regions are well served by public transport.

##  Why I Chose This Topic

As an international student, I rely heavily on buses for daily commuting. When I first arrived, it was hard to know which areas had good bus access. So I wanted to find out where bus services already exist, and more importantly, which residential or key zones (schools, hospitals, etc.) do **not** have coverage.

##  Tools and Data Sources

All data was downloaded from official sources such as:

- Waikato Open Data Hub
- Stats NZ Geographic Data Service
- LINZ Data Service

Key datasets include:

- Hamilton City boundary
- Bus stops and bus routes
- Residential, school, hospital, and commercial areas
- Water bodies and protected zones
- Existing road network

*(Full dataset details and links are in the Appendix section.)*

##  Research and Analysis Logic

1. **Buffer Analysis**  
   Created 300m, 400m, and 500m buffers around bus stops to define service areas.

2. **Identify Uncovered Areas**  
   Subtracted buffer zones from the Hamilton City boundary and from key zones (residential, school, hospital, etc.) to find areas without service.

3. **Refine Results**  
   Removed water bodies and protected areas from the uncovered zones.

4. **Accessibility Check**  
   Filtered out regions without roads to focus on reachable areas.

5. **Repeat for Multiple Buffer Distances**  
   Repeated steps above for 300m, 400m, and 500m to compare service gaps under different assumptions.

##  Results

| Buffer Distance | Total Uncovered Area (m²) | Uncovered in Key Zones (m²) |
|-----------------|---------------------------|------------------------------|
| 300 meters      | 38,171,365                | 9,824,573                   |
| 400 meters      | 29,523,099                | 4,478,612                   |
| 500 meters      | 24,446,065                | 2,390,834                   |

- The maps clearly show that as buffer size increases, uncovered areas shrink.
- Red zones on the map indicate important places (like residential or schools) with no bus service—these should be prioritized for future planning.
- Increasing buffer size improves coverage on paper, but may reduce the accuracy of identifying real gaps in high-priority areas.

##  Limitations

- Source datasets had different resolutions and update times, which may affect accuracy.
- Did not consider population distribution, real travel behavior, or physical barriers (rivers, elevation).
- Buffer zones are an approximation—they don’t reflect real walking conditions or accessibility.

##  Future Work

To improve the project:

- Apply **network-based accessibility** instead of buffer zones.
- Add **population and demographic data** to identify high-demand zones.
- Include **bus frequency and schedule** data to reflect actual service availability.
- Consider building an **interactive web map** using ArcGIS Online or Leaflet for better user experience.
- Automate the workflow and build a **user interface** that displays key zone names, roads, and statistics on hover.

##  Files Included

- `Report.pdf` – Detailed research report with maps and data analysis
- `Poster.pptx` – Summary poster for presentation
- `analysis_script.ipynb` – Python script automating spatial data preprocessing and summary extraction

##  Appendix: Dataset Sources

| Dataset | Description | Source |
|--------|-------------|--------|
| Bus Stops | Existing stop points | [Waikato Open Data Hub](https://data-waikatolass.opendata.arcgis.com/datasets/b143a38c66bb43e6a05ffe0f3bf9a735_0/explore) |
| Bus Routes | Existing route lines | [Waikato Open Data Hub](https://data-waikatolass.opendata.arcgis.com/datasets/7746870286744b7ab77fc44291c34123_0/explore) |
| Hamilton City Boundary | Analysis extent | [Stats NZ](https://datafinder.stats.govt.nz/layer/120963-territorial-authority-2025/) |
| Residential Zones | Key priority area | [LINZ Data Service](https://data.linz.govt.nz/layer/50325-nz-residential-area-polygons-topo-150k/) |
| Schools & Hospitals | Key priority area | [LINZ Data Service](https://data.linz.govt.nz/layer/105588-nz-facilities/) |
| Roads | Existing road network | [LINZ Data Service](https://data.linz.govt.nz/layer/53382-nz-roads-addressing/) |
| Rivers, Lakes, Reserves | Exclusion areas | Multiple sources from LINZ and Waikato Open Data Hub |

---

