# EEG Data Collection Protocol (Emotiv EPOC X – 14 Channels)

## Overview
This protocol describes how to collect EEG data for mapping 10 distinct imagined actions to the 10 most frequent English letters (E, T, A, O, I, N, S, H, R, D).  
- Device: **Emotiv EPOC X (14 channels)**  
- Participants: **12–15 volunteers**  
- Goal: Build dataset for letter-based communication via motor imagery.  
- Accessibility: Designed for mute, paralyzed, and blind individuals (no reliance on speech or vision).  

---

## Actions to Letters Mapping

| Letter | Imagined Action | Notes |
|--------|-----------------|-------|
| **E** | Right-hand punch | Imagine driving your right fist forward. |
| **T** | Left-hand grasp | Imagine closing your left hand into a fist and squeezing. |
| **A** | Right-foot kick | Imagine swinging your right foot forward to kick. |
| **O** | Both-feet jump | Imagine pushing off the ground with both feet to jump. |
| **I** | Tongue press | Imagine pressing your tongue firmly to the roof of your mouth. |
| **N** | Jaw clench | Imagine biting down hard with your teeth. |
| **S** | Lip purse | Imagine pursing your lips tightly, as if to whistle. |
| **H** | Shoulder shrug | Imagine lifting both shoulders upward toward your ears. |
| **R** | Head nod | Imagine nodding your head up and down (yes gesture). |
| **D** | Brow raise | Imagine lifting your eyebrows upward as if in surprise. |
| **Control**    | Rest/neutral       | Stay relaxed, blank mind, no imagery. |

---

## Trial Structure

- **Trial length:** 3 seconds imagery + 2 seconds rest  
- **Cue method:** On-screen text for sighted users; audio tone/vibration cues for blind/paralyzed users  
- **Trials per action per participant:** 80–100  
- **Total per participant:** 10 actions × 100 trials = ~1,000 trials  
- **Total across 12 participants:** ~12,000 trials  

---

## Session Plan

- **Sessions per participant:** 2–3 (to reduce fatigue and capture day-to-day variability)  
- **Per session:** ~30–40 trials per action (~300–400 trials total)  
- **Breaks:** 5–10 minutes every 100–150 trials  

---

## Data Management

- **Sampling rate:** ≥128 Hz (native to EPOC X)  
- **Format:** Save as EDF/CSV with clear metadata (participant ID, action label, trial number, timestamp)  
- **Labeling convention:**  
  - `participantXX_actionYY_trialZZ.csv`  
  - Example: `P01_E_trial034.csv`  
- **Metadata file:** Store demographics (age, gender, handedness) without personal identifiers.  

---

## Notes
- Emphasize **kinesthetic imagery** (feel the movement, don’t visualize it from outside).  
- Instruct participants to avoid **actual movement**, blinking, or jaw tightening unless that is the imagery.  
- Use **consistent cues and timing** across all sessions to reduce variability.  
