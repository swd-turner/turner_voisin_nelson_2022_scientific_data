[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.11584567.svg)](https://doi.org/10.5281/zenodo.11584567)

# RectifHyd—monthly generation estimates for 1,500 hydroelectric power plants in the United States

Sean Turner<sup>1</sup>, Nathalie Voisin<sup>2\*</sup>, and Kristian
Nelson<sup>2</sup>, Cameron Bracken<sup>2\*</sup>

<sup>1 </sup> Oakridge National Laboratory <sup>2 </sup> Pacific
Northwest National Laboratory

\* Contacts: <turnersw@ornl.gov> <cameron.bracken@pnnl.gov>
<nathalie.voisin@pnnl.gov>

## Abstract

The U.S. Energy Information Administration conducts an annual survey
(form EIA-923) to collect, among other variables, annual and monthly net
generation for more than ten thousand U.S. power plants. Only ~10% of
the ~1,500 hydroelectric plants included in this regular data release
come with observations of monthly net generation; the remaining 90% of
plants are represented with monthly net generation that is imputed using
a statistical method. The imputation method neglects local hydrology and
reservoir operations, rendering the monthly generation data unsuitable
for several research applications. Here we present an alternative
approach to disaggregate each plant’s reported annual generation using
historical reservoir releases (~180 plants) or, for the majority of
cases where reservoir releases are unavailable, river discharge recorded
downstream of each dam (~1180 plants). We evaluate the approach using
130 plants for which monthly generation observations are available,
showing median Kling Gupta Efficiency (KGE) of 0.74, 90% CI \[-0.07,
0.93\] across plants with observed reservoir release, and KGE of 0.51
\[-0.28, 0.79\] for cases imputed using a downstream flow gage. The new
dataset—named RectifHyd—provides a timely alternative to EIA-923 for
U.S. scale, plant-level, hydropower net generation for analyzing
within-year hydropower generation behavior and constraining sub-annual
hydropower availability in power grid operation and expansion models.

## Journal reference

Turner, S.W.D., Voisin, N. & Nelson, K. Revised monthly energy
generation estimates for 1,500 hydroelectric power plants in the United
States. Sci Data 9, 675 (2022).
<https://doi.org/10.1038/s41597-022-01748-x>

## Data reference

Turner, S., Voisin, N., Nelson, K., & Bracken, C. (2024). RectifHyd
(1.3) \[Data set\]. Zenodo. <https://doi.org/10.5281/zenodo.11584567>

### Data download

In R:

    readr::read_csv("https://zenodo.org/records/11584567/files/RectifHyd_v1.3.csv")

In Python:

    import pandas as pd
    pd.read_csv("https://zenodo.org/records/11584567/files/RectifHyd_v1.3.csv")

### Reproduce RectifHyd

1.  Clone this repo to get all scripts.
2.  Download each of the following datasets and place in the `data`
    directory.

-   **ResOpsUS**: Steyaert, J., Condon, L., Turner, S. & Voisin, N.
    (2021). ResOpsUS \[Data set\]. Zenodo.
    <https://doi.org/10.5281/zenodo.5367383>
-   **EIA-923**: U.S. Energy Information Administration (2023).
    EIA-923/906/920. \[Data set\]. EIA.
    <https://www.eia.gov/electricity/data/eia923/> (all spreadsheets
    2001 - 2022)
-   **HILARRI**: Hansen, C.H., and P.G. Matson. 2021. Hydropower
    Infrastructure - LAkes, Reservoirs, and Rivers (HILARRI). DOI:
    10.21951/HILARRI/1781642
-   **Existing Hydropower Assets**: Megan M. Johnson, Shih-Chieh Kao,
    and Rocio Uria-Martinez. 2023. Existing Hydropower Assets, 2023.
    HydroSource. Oak Ridge National Laboratory, Oak Ridge, Tennessee,
    USA. <https://doi.org/10.21951/EHA_FY2023/1972057>
-   **NWIS**: U.S. Geological Survey, 2016, National Water Information
    System data available on the World Wide Web (USGS Water Data for the
    Nation), accessed \[September, 2023\] via R package
    \[<http://waterdata.usgs.gov/nwis/>\].

1.  Run the following R scripts in the main directory to re-create this
    dataset:

<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 82%" />
</colgroup>
<thead>
<tr class="header">
<th>Script Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>1a. Process EIA spreadsheets.R</code></td>
<td>Combine each of the last 20 years’ <code>EIA-923</code> data
releases, extract hydropower net generation, output clean data table as
.csv</td>
</tr>
<tr class="even">
<td><code>1b. Download gauge flow.R</code></td>
<td>Combine each of the last 20 years’ <code>EIA-923</code> data
releases, extract hydropower net generation, output clean data table as
.csv</td>
</tr>
<tr class="odd">
<td><code>2a Disaggregate using release.R</code></td>
<td>Prepare data to disaggregate annual hydropower using reservoir
releases from <code>ResOpsUS</code></td>
</tr>
<tr class="even">
<td><code>2b Disaggregate using USGS.R</code></td>
<td>Prepare data to disaggregate annual hydropower using downstream
flows</td>
</tr>
<tr class="odd">
<td><code>3. Combine and compute new monthly generation.R</code></td>
<td>Combine flow fraction tables and perform disaggregation of annual to
monthly flow</td>
</tr>
<tr class="even">
<td><code>4a. Create final file.R</code></td>
<td>Clean up and prepare the final RectifHyd file</td>
</tr>
</tbody>
</table>

Enjoy!

ST | NV | KN | CB
