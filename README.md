# Nibras
## EEG-Based Communication System for Non-Verbal Individuals  
**Senior Project – CS499**  
Prince Sultan University  

---

## Problem Statement
Communication is a fundamental human right, yet many individuals with severe disabilities (mute, paralyzed, blind) are unable to express themselves verbally or through movement. While EEG-based brain–computer interfaces (BCIs) have shown promise in enabling communication, most existing solutions depend on visual stimuli (e.g., flashing letters) or speech-motor imagery, which excludes parts of this population. There is a need for an accessible system that uses **pure motor imagery** of distinct actions to map directly to letters, allowing individuals to build words and sentences without reliance on speech or vision.

---

## Project Objectives
- Develop a **motor imagery–based EEG communication prototype** using Emotiv EPOC X.  
- Map **10 distinct imagined actions** to the most frequent letters in English.  
- Collect EEG data from multiple volunteers and create a new dataset tailored to this use case.  
- Train and evaluate ML models to classify imagined actions with sufficient accuracy.  
- Produce a **research paper** describing the methodology, experiments, results, and limitations.  
- Build a **prototype interface** that demonstrates how classified actions can form words/sentences.  

---

## Earlier/Similar Work
- **P300 and SSVEP spellers**: Well-studied systems that rely on flashing grids or flickering stimuli to detect letter choice. They achieve good accuracy but require intact vision and may cause fatigue.  
- **Motor imagery BCI**: Typically limited to binary or 3–4 class systems (e.g., left hand, right hand, feet). Rarely extended to higher numbers of actions due to overlap and signal noise.  
- **Commercial devices**: Products like Emotiv Insight/EPOC and OpenBCI have been used in research and hobbyist projects, but most focus on simple commands or game control, not multi-letter communication.  
- **Inspiration**: A Twitch streamer who used EEG signals mapped to actions to play *Elden Ring*. This showed the feasibility of translating imagined movements into distinct, usable control signals.  

---

## Project Tasks and Group Contribution
This project will be carried out jointly by the team:  
- **Ahmed Ibrahim, Anas Houri, and Tareq Ghazi** – Senior CS students at Prince Sultan University, all with backgrounds in AI/ML/NLP.  
- Supervised by **Dr. Moataz Billah Nagoudi**, an NLP expert with widely used models.  

At this stage, the work is considered **group-level contribution**; task-level breakdown will be added later.

---

## Project Execution Plan with Milestones (CS499 Timeline)

**Week 3–4 (September)**  
- Form A submission (team formation, project idea)  
- Literature review on EEG-based spellers and motor imagery  

**Week 5 (Mid-September)**  
- Form B submission (proposal with objectives, plan, milestones)  
- Define final set of imagined actions and letters  

**Week 7 (Late September)**  
- Project planning and requirements analysis  
- Initial survey/testing of EEG setup feasibility with 1–2 volunteers  

**Week 9 (October)**  
- Project design and system modeling  
- Build pipeline for data collection and preprocessing (including artifact removal) 

**Week 11 (Mid-October)**  
- Start data collection (pilot with 4–5 volunteers)  
- Begin initial experiments with ML models  

**Week 12–13 (Late October – Early November)**  
- Expanded data collection (target 12–15 volunteers, ~100–120 trials per action)  
- Train and evaluate different classifiers (CNN, RNN, etc.)  
- Testing and experimental evaluation  

**Week 14 (Mid-November)**  
- Prototype development (simple interface to demonstrate word/letter spelling)  
- Documentation of results, limitations, and findings  

**Week 15 (End of November)**  
- Final demo and project presentation  
- Research paper submission  
- Project report and documentation delivery  

:contentReference[oaicite:1]{index=1}

---

## Expected Deliverables per Stage
- **Week 5:** Project proposal with objectives, methods, timeline  
- **Week 7:** System design and data collection pipeline + Receiving and Preparing EEG Headsets  
- **Week 10:** Initial dataset and pilot classification results  
- **Week 13:** Expanded dataset, trained models, evaluation results  
- **Week 14:** MVP prototype of speller interface + draft research paper  
- **Week 15:** Final paper, documentation, and project presentation  

---

## Motivation
Our motivation is to **help people in need**, especially those with severe disabilities who cannot communicate verbally or physically. By leveraging our background in AI/ML and our access to EEG hardware, we aim to demonstrate that even within limited resources, **non-invasive BCIs** can make a tangible difference in accessibility and inclusivity.

---

## Inspiration
We were inspired by a Twitch streamer who successfully controlled a complex game (*Elden Ring*) using an EEG headset by mapping imagined actions to in-game commands. This showed that even consumer-grade EEG devices can support creative and impactful applications. We want to extend this idea into a socially meaningful domain: **accessible communication**.

---

## Limitations & Considerations
- **Signal noise and variability**: EEG signals are weak, noisy, and differ across individuals.  
- **Overlap of motor imagery actions**: Some imagined movements may produce similar signals, making classification difficult.  
- **Limited dataset size**: Collecting enough clean, labeled data within one semester may be challenging.  
- **Hardware constraints**: Emotiv EPOC X has 14 channels—not as precise as clinical-grade EEG.  

We will also remain mindful of **data privacy and anonymization**, though the main emphasis is on technical limitations.

---

## Expected Outcomes
- Primary goal: Demonstrate classification of **10 imagined actions mapped to 10 letters** with measurable accuracy.  
- Expected deliverables: Dataset, trained ML models, MVP prototype, and a research paper.  
- Realistic expectation: A proof-of-concept system showing feasibility, even if full accuracy is not achieved within the semester timeframe.  
