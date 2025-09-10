# EEG Headset Benchmark (Condensed) — Visual Snapshot

> Source: Our internal “EEG Devices” benchmark sheet (latest entries summarized below).

## At-a-Glance Table

| Company    | Model                 | Price         | Channels | Battery Life | Raw Data Access           | Ease of Setup | Notes (from our sheet) |
|------------|-----------------------|---------------|----------|--------------|---------------------------|---------------|------------------------|
| **Emotiv** | Insight               | $500          | 5        | 20 hrs       | 2–3 weeks*                | Easy          | *Emailed re: faster shipping |
| **Emotiv** | **EPOC X**            | **$999**      | **14**   | 9 hrs        | 2–3 weeks*                | Easy          | **Used often in research contexts** |
| **Emotiv** | MN8                   | $399          | 2        | 6 hrs        | 2–3 weeks*                | Easiest       | Inadequate for research purposes |
| Neurosity  | Crown                 | $1,499        | 8        | 3 hrs        | 2–3 weeks                 | Easy          | BLE, lifetime membership (per vendor) |
| BrainBit   | Headband              | **1,900 SAR** | 4        | 12 hrs       | Free SDK (raw data)       | Easy          | Provides raw data via free SDK |
| NeuroSky   | MindWave Mobile 2     | $130          | 1        | 12 hrs       | —                         | Easy          | Inadequate for research purposes |
| **CGX**    | Patch EEG             | $750          | 2        | 14 hrs       | ~5 business days          | Easiest       | — |
| **CGX**    | Dev Kit (8-ch)        | Inquired      | 8        | 8 hrs        | Inquired                  | Moderate      | Demos possible on request |
| Mindrove   | Arc 2                 | $779          | 6        | 4–6 hrs      | 2–3 weeks                 | Easy          | — |
| Mindrove   | Bright 2              | $679          | 4+2      | 4–6 hrs      | 6–8 weeks                 | Easy          | — |

\* “2–3 weeks” indicates the **shipping/lead-time** entries we recorded while checking availability.

---

## Relevance to Our Use Case (Motor Imagery → Letters)

- **Channels matter for separability.** We target **10 distinct imagined actions** (no SSVEP, no speech), so devices below ~8 channels are risky; **14 channels** gives better spatial coverage and more robust features.
- **Research viability over comfort-only headbands.** Consumer bands (1–5 channels) are great for meditation/focus apps, but our task (multi-class motor imagery classification) needs **research-leaning hardware** with stable signals and decent density.
- **Practical session length.** Battery life ≥ 8–9 hours is sufficient for our planned sessions (3 s imagery / 2 s rest, 80–120 trials per class across 2–3 days).

---

## Why We’re Going with **Emotiv EPOC X**

1. **Channel Count & Coverage:** **14 channels** strike a good balance between signal richness and setup time—well-suited for separating hand/foot/orofacial/shoulder/head imagery without a clinical cap.
2. **Proven in Research:** EPOC line is **widely used in academic studies** and community BCIs; consistent ecosystem and documentation make it reliable for a semester-long project.
3. **Ease of Use:** Quick setup with saline sensors; practical for collecting **thousands of trials** across volunteers without complex gel-based prep.
4. **Software Ecosystem:** While raw data export requires **EmotivPRO**, the tooling is mature for acquisition, labeling, and streaming—useful for our data pipeline and MVP.
5. **Battery & Wireless:** ~**9 hours** continuous use covers long recording days; wireless comfort reduces fatigue for volunteers.

> Taken together, **EPOC X** offers the **best blend of data quality, channel density, usability, and time-to-productive-data** for our Motor Imagery speller MVP this semester.

---
