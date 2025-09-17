# EEG Preprocessing Notes (Motor Imagery Focus)

## **1. Bandpass Filtering (8–30 Hz)**
- **Purpose:** Isolates motor imagery (MI)–relevant rhythms.  
- **Targeted Frequencies:**  
  - **µ rhythm (8–12 Hz):** From motor cortex, suppressed during real/imagined movement.  
  - **β rhythm (13–30 Hz):** Related to motor control and planning, modulated during MI.  
- **Why exclude others:**  
  - Below 8 Hz → dominated by eye movements (EOG) and slow drifts.  
  - Above 30 Hz → often muscle activity (EMG) and high-frequency noise.  
- **Implementation:**  
  - Apply FIR/IIR bandpass filter with cutoff at [8, 30] Hz.  
  - Retains brain activity relevant for MI classification.

---

## **2. Notch Filtering (50/60 Hz)**
- **Purpose:** Remove power line interference.  
- **Frequency:**  
  - 50 Hz in most countries, 60 Hz in North America.  
  - Harmonics (100, 150 Hz, etc.) may also need suppression.  
- **Implementation:**  
  - Apply narrowband notch filter centered at 50/60 Hz.  
  - Minimally affects neighboring frequencies while removing sinusoidal noise.  
- **Alternatives:**  
  - Regression/adaptive methods (e.g., EEGLAB’s *CleanLine*) for more flexible artifact removal.

---

## **3. Independent Component Analysis (ICA)**
- **Purpose:** Separate mixed EEG signals into independent sources (neural + artifacts).  
- **Process:**  
  1. Decompose EEG into independent components (ICs).  
  2. Inspect each IC by its **time course, frequency spectrum, and scalp map**.  
     - Eye blinks → strong frontal ICs with spike-like time series.  
     - Muscle activity → high-frequency, localized ICs.  
     - ECG → periodic sharp peaks.  
  3. Identify artifact ICs and remove them.  
  4. Reconstruct EEG using only clean ICs.  
- **Benefit for MI:**  
  - Removes EOG/EMG/ECG contamination without distorting oscillations in motor cortex.  
  - Preserves key µ and β rhythms critical for MI decoding.
- **Available Implementations:**  
  - **Python:** [`mikbuch/bss_ica_eeg`](https://github.com/mikbuch/bss_ica_eeg) — Python implementation of ICA, Uses MNE-Python to apply ICA for artifact removal in EEG.  

---

## **4. Artifact Subspace Reconstruction (ASR)**
- **Purpose:** Automated cleaning method to detect and correct artifacts in real time.  
- **How it works:**  
  1. Build a baseline model from clean EEG (e.g., 1–2 minutes of resting state with minimal artifacts).  
  2. Slide through EEG in short windows (e.g., 0.5–1 sec).  
  3. Compare each window’s variance to the baseline covariance.  
  4. If variance exceeds a threshold (e.g., 5–10× baseline), mark as artifact.  
  5. Project contaminated data into a “clean” subspace and reconstruct.  
- **Baseline Collection:**  
  - Subject seated still, headset stable, eyes open (fixation) or closed consistently.  
  - Normal blinking allowed, but no large movements, jaw clenching, or talking.  
  - Record 1–2 minutes in a quiet, controlled environment.  
- **Threshold Tuning:**  
  - Too low (e.g., 2–3×): Overcorrection, loss of real MI rhythms.  
  - Too high (e.g., >15×): Artifacts remain.  
  - Typical range: **5–10× baseline variance (≈ 5 SD default in EEGLAB)**.  
- **Limitations:**  
  - Requires a good baseline — if contaminated, ASR misclassifies artifacts.  
  - Thresholds need to be tuned per dataset.  
- **Benefit for MI:**  
  - Removes unpredictable, non-stationary artifacts (blinks, movements).  
  - Preserves more usable data compared to discarding entire trials.  
- **Available Implementations:**  
  - **Python:** [`DiGyt/asrpy`](https://github.com/DiGyt/asrpy) — Python implementation of ASR, mirrors MATLAB version, suitable for MI preprocessing pipelines.  
  - **MATLAB/EEGLAB:** `clean_rawdata` plugin, widely used and validated.  

---

⚡ **Current MI preprocessing pipeline:**  
**Bandpass (8–30 Hz) → Notch (50/60 Hz) → ICA → ASR (optional or complementary).**
