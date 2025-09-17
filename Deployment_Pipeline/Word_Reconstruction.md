# Word Reconstruction in Real-Time EEG-to-Speech

In this project, once letters are predicted from EEG signals, a **word reconstruction step** ensures that errors are minimized before the text is sent to Text-to-Speech (TTS). This is crucial because the patient will use the system for real-time communication.

Since TTS will be triggered **immediately after each word**, the reconstruction must be **efficient and incremental** (no rewriting of past words).

---

## Approaches to Correction

| Approach        | Pros                                                                 | Cons                                                                 | Suitability |
|-----------------|----------------------------------------------------------------------|----------------------------------------------------------------------|-------------|
| **Word-based**  | - Low latency <br> - Immediate feedback <br> - Good for spelling errors <br> - Efficient for real-time | - Limited context (can’t fix grammar/semantic errors across words) | ✅ Best fit for real-time TTS |
| **Sentence-based** | - Highest accuracy <br> - Fixes grammar and semantics <br> - Useful for offline transcripts | - High latency (requires full sentence) <br> - Heavy computation <br> - Confusing if text changes after speech | ❌ Not suitable for real-time |
| **Hybrid**      | - Balance: quick feedback + later refinement <br> - Can fix grammar after the fact | - UI complexity (rewrites can confuse patient) <br> - Adds extra compute | ⚠️ Only viable if post-sentence polishing is acceptable |

---

## Model Choices for Word Reconstruction

| Model Type              | Pros                                                | Cons                                                   | Best Use Case |
|--------------------------|----------------------------------------------------|--------------------------------------------------------|---------------|
| **n-gram LM (Char/Word)** | - Extremely fast <br> - Very lightweight <br> - Easy to train | - Limited context (short history) <br> - Weak for rare words | Baseline real-time correction |
| **Small RNN (LSTM/GRU)** | - Supports longer context <br> - Incremental decoding | - Slightly heavier than n-grams <br> - Still weaker than Transformers | Streamable, better than n-grams |
| **Compact Transformer (causal, e.g. DistilGPT-2 small)** | - Strong language modeling <br> - Can capture longer dependencies | - More compute <br> - Needs optimization for real-time | When stronger LM is needed but latency budget allows |
| **BERT/Masked LM**       | - Excellent at sentence-level correction <br> - Strong semantic understanding | - Needs future context (not streamable) <br> - High latency and compute | Offline or sentence-level polishing only |

---

## Summary

For this project, **word-based reconstruction with either an n-gram LM or a small RNN/Transformer LM** is the best trade-off. BERT and sentence-level correction approaches are not suitable for real-time speech because they require full-sentence context and introduce unacceptable latency.
