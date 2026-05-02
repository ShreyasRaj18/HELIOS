```Contributed in the project whilst in the Hackathon.```
---


# HELIOS — Halo Event Locator & Identification of Solar-CMEs

**HELIOS** (Halo Event Locator & Identification of Solar-CMEs) is a research-driven project combining **CACTus CME catalogs** with **in-situ particle data** from the **Solar Wind Ion Spectrometer (SWIS)**, part of the **ASPEX payload onboard Aditya-L1**.  

Our goal: to detect and forecast **halo CMEs** using **particle signatures in the solar wind**, providing lead time to protect satellites, navigation systems, and terrestrial power grids.

---

## Scientific Background

- **Coronal Mass Ejections (CMEs):**  
  Huge expulsions of plasma and magnetic fields from the solar corona, carrying billions of tons of material into the heliosphere.  

- **Halo CMEs:**  
  A special class of CMEs that appear to surround the Sun in coronagraph images, often Earth-directed. They are the **most geoeffective** because they travel directly along the Sun–Earth line.  

- **Solar Wind Parameters (measured by SWIS):**
  - **Number Density (n):** plasma concentration, often spikes during CME shocks.  
  - **Velocity (v):** CME ejecta typically travel faster than the background solar wind (≈ 400 km/s), sometimes exceeding 1000 km/s.  
  - **Temperature (T):** CME plasma often has enhanced proton temperatures.  
  - **Flux (Φ):** measures the flow of solar particles per unit time, sensitive to CME arrival.  

- **Derived Physical Quantity — Dynamic Pressure:**  
  The impact of the solar wind on the magnetosphere depends on  
  \[
  P_{dyn} = \rho v^2 = n m_p v^2
  \]  
  where \( n \) is the proton density, \( v \) is solar wind speed, and \( m_p \) is proton mass.  
  CMEs drive sudden increases in **dynamic pressure**, compressing Earth’s magnetosphere and triggering geomagnetic storms.  

---

## Project Objectives

1. **Labeling CMEs:** Use **CACTus CME catalog** (LASCO/SOHO) to extract halo event timestamps.  
2. **Data Extraction:** Ingest **SWIS Level-2 CDF data** (flux, density, temperature, velocity) from Aditya-L1.  
3. **Feature Engineering:**  
   - Moving averages, rolling gradients, variance.  
   - Physics-guided features like **dynamic pressure**, proton beta proxies, and volatility.  
4. **Machine Learning Forecasting:**  
   - Train supervised models (RandomForest, GradientBoosting) on event vs. non-event windows.  
   - Evaluate with **time-ordered cross-validation** to avoid leakage.  
5. **Outcome:** An operational pipeline to forecast CME arrival hours before Earth impact.  

---

## Novelty

- First attempt to **fuse coronagraph-derived halo CME events (CACTus)** with **in-situ particle signatures (SWIS, Aditya-L1)**.  
- Moves beyond thresholds → integrates **physics + ML** for robust early-warning.  
- Potential to extend from **detection → forecasting**, critical for space-weather operations.  

---

## Dataset Sources

1. **CACTus CME Catalog (LASCO/SOHO):**  
   Automated recognition of CMEs, listing onset time, angular width, speed, and halo flag.  
   → [CACTus Catalog](https://www.sidc.be/cactus/catalog/LASCO/)  

2. **Aditya-L1 / SWIS Level-2 Data (ISSDC):**  
   Measures solar wind particle flux, density, temperature, speed.  
   → [ISSDC Portal](https://www.issdc.gov.in/)  

3. **CDF Libraries (NASA SPDF):**  
   Standard format for SWIS Level-2 files.  
   → [cdflib](https://pypi.org/project/cdflib/)  

---

## References

- Robbrecht, E., & Berghmans, D. (2004). *Automated recognition of CMEs (CACTus).* A&A 425, 1097–1106.  
- Gopalswamy, N. (2006). *Properties of Interplanetary CMEs.* Space Sci Rev 124, 145–168.  
- ISRO — [Aditya-L1 Mission](https://www.isro.gov.in/Aditya_L1.html)  
- ISRO — [ASPEX/SWIS Instrument](https://www.isro.gov.in/Spacecraft/Aditya_L1_ASPEX.html)  
- NASA SPDF CDF Tools: [https://spdf.gsfc.nasa.gov/pub/software/cdf/](https://spdf.gsfc.nasa.gov/pub/software/cdf/)  

---

## Tech Stack

- **Languages:** Python, C (optional)  
- **Libraries:** Pandas, NumPy, SciPy, scikit-learn, Matplotlib, Plotly, cdflib  
- **Methods:** Signal processing, statistical thresholds, ML classification, anomaly detection  

---
