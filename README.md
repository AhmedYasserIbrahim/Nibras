# Nibras
## 🧠 EEG-Based Communication System for Non-Verbal Individuals  
**Senior Project – CS499**  
Prince Sultan University 

---

## ❓ Problem Statement
Communication is a fundamental human right, yet many individuals with severe disabilities (mute, paralyzed, blind) are unable to express themselves verbally or through movement. While EEG-based brain–computer interfaces (BCIs) have shown promise in enabling communication, most existing solutions depend on visual stimuli (e.g., flashing letters) or speech-motor imagery, which excludes parts of this population. There is a need for an accessible system that uses **pure motor imagery** of distinct actions to map directly to letters, allowing individuals to build words and sentences without reliance on speech or vision.

---

## 🎯 Project Objectives (Chronological)
1. Conduct a **literature review** on EEG-based spellers and motor imagery.  
2. Define the **set of imagined actions** and finalize system requirements.  
3. Design and implement a **data collection pipeline**.  
4. Collect EEG data from multiple volunteers to build a **custom dataset**.  
5. Train and evaluate **ML models** (CNN, RNN, etc.) for classification.  
6. Build an **MVP prototype interface** for spelling letters into words.  
7. Write a **research paper** documenting methodology, experiments, and findings.  
8. Deliver the **final presentation and report**.  

---

## 📚 Earlier/Similar Work

- ### **[EEG-Based Brain-Computer Interfaces Using Motor-Imagery: Techniques and Challenges** (2019)] (https://www.mdpi.com/1424-8220/19/6/1423)  
This paper reviews how motor imagery (MI) can be used in brain-computer interfaces. It explains how imagining limb movements changes EEG rhythms and outlines methods for processing and classifying these signals, such as preprocessing, feature extraction, and machine learning. It also discusses the main challenges, like signal noise and differences between users. This work is relevant to us because it provides useful methods for handling EEG data and supports our focus on MI as the core of our communication system.

- ### **[A State-of-the-Art Review of EEG-Based Imagined Speech Decoding** (2022)] (https://www.frontiersin.org/articles/10.3389/fnhum.2022.867281/full)  
This review looks at research that uses EEG to decode imagined speech as a way for people with disabilities to communicate. Most of the surveyed work relies on imagined speech (silently thinking words) instead of motor imagery, which is our approach. Many studies used older models like SVM and often had low accuracy, especially for multi-class tasks. Even so, the paper is a useful benchmark, giving us results to compare against and showing the advantages of choosing MI over imagined speech.

- ### **[A study of motor imagery EEG classification based on feature fusion and attentional mechanisms** (2025)] (https://www.frontiersin.org/articles/10.3389/fnhum.2025.1611229/full)  
This recent paper proposes a deep learning model for motor imagery EEG classification. The model combines different features with attention mechanisms and achieves high accuracy while staying lightweight. Although it is not designed for our exact use case, it gives us ideas for building efficient models that can run in real time. We see this work as a helpful reference for designing and improving our own classification system.

- ### **[Perrikaryal EEG Gaming Demonstration** (2023)] (https://spectrum.ieee.org/elden-ring-hands-free-controller)  
Twitch streamer Perrikaryal showed how the **Emotiv EPOC X headset** can be used in real time to play *Elden Ring* with EEG signals. She mapped brain signal patterns to game actions, proving that online EEG classification is possible with consumer hardware. While not academic research, this demonstration is directly relevant to us because it uses the same headset and setup style we plan to use. It inspired our project and supports the feasibility of extending this approach from gaming to communication.


---

## 👥 Project Tasks and Group Contribution
This project will be carried out jointly by the team:  
- **Ahmed Ibrahim, Anas Houri, and Tareq Ghazi** – Senior CS students at Prince Sultan University, all with backgrounds in AI/ML/NLP.  
- Supervised by **Dr. Moataz Billah Nagoudi**, an NLP expert with widely used models.  

At this stage, the work is considered **group-level contribution**; task-level breakdown will be added later.

---

## 📅 Project Execution Plan with Milestones

**Week 3–4 (September)**  
- Team formation & idea confirmation  
- Start literature review  

**Week 5 (Mid-September)**  
- Submit proposal (Form B)  
- Finalize imagined actions and system requirements  

**Week 7–8 (Late September)**  
- System design & data collection pipeline implementation  

**Week 9–10 (Early October)**  
- Pilot data collection (4–5 volunteers)  
- Initial preprocessing and feature exploration  

**Week 11–12 (Mid October)**  
- Expanded data collection (target 12–15 volunteers, ~100 trials/action)  
- Begin model training and evaluation  

**Week 13 (Late October – Early November)**  
- Continue model testing  
- Refine dataset quality and address limitations  

**Week 14 (Mid-November)**  
- Prototype development (speller interface)  
- Start drafting research paper  

**Week 15 (End of November)**  
- Finalize research paper and documentation  
- Deliver final demo and presentation  

---

## 📦 Expected Deliverables
- **Week 5:** Project proposal with objectives, methods, timeline  
- **Week 8:** System design and functional data pipeline  
- **Week 10:** Pilot dataset + preprocessing results  
- **Week 12:** Expanded dataset + initial model results  
- **Week 13:** Refined evaluation results, error analysis  
- **Week 14:** MVP prototype + draft research paper  
- **Week 15:** Final paper, documentation, and project presentation  

---

## 💡 Motivation
Our motivation is to **help people in need**, especially those with severe disabilities who cannot communicate verbally or physically. By leveraging our background in AI/ML and our access to EEG hardware, we aim to demonstrate that even within limited resources, **non-invasive BCIs** can make a tangible difference in accessibility and inclusivity.

---

## 🌟 Inspiration
We were inspired by a Twitch streamer who successfully controlled a complex game (*Elden Ring*) using an EEG headset by mapping imagined actions to in-game commands. This showed that even consumer-grade EEG devices can support creative and impactful applications. We want to extend this idea into a socially meaningful domain: **accessible communication**.

---

## ⚠️ Limitations & Considerations
- **Signal noise and variability**: EEG signals are weak, noisy, and differ across individuals.  
- **Overlap of motor imagery actions**: Some imagined movements may produce similar signals, making classification difficult.  
- **Limited dataset size**: Collecting enough clean, labeled data within one semester may be challenging.  
- **Hardware constraints**: Emotiv EPOC X has 14 channels—not as precise as clinical-grade EEG.  

We will also remain mindful of **data privacy and anonymization**, though the main emphasis is on technical limitations.

---

## ✅ Expected Outcomes
- **Primary goal:** Demonstrate classification of **10 imagined actions mapped to 10 letters** with measurable accuracy.  
- **Expected deliverables:** Dataset, trained ML models, MVP prototype, and a research paper.  
- **Realistic expectation:** A proof-of-concept system showing feasibility, even if full accuracy is not achieved within the semester timeframe.  

---

## 🔗 Relevant Links
- [Execution Plan (GitHub)](https://github.com/AhmedYasserIbrahim/Nibras/blob/main/Execution_Plan.md)  
- [EEG Headset Benchmark (GitHub)](https://github.com/AhmedYasserIbrahim/Nibras/blob/main/EEG_Headset_Benchmark.md)  
