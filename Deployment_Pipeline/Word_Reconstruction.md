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

## Summary

For this project, **word-based reconstruction** will most probably be our go-to choice. Spelling correction for words one by one is necessary, as we aim to implement a text to speech model after this step in the pipeline. Even though the sentence based model may improve the overall accuracy as it relies on the context for spelling correction, it would be inconvenient to wait for the user to formulate the entire sentence before running the auto correction and then converting it to audible speech. One potential solution is to look for a model that relies on the past context to correct the current word, without looking at the sentence as a whole. For example: "I eat aple" -> When the model is constructing "aple" it looks at the past couple of words in a way similar to n-gram models. This is to be discussed with Dr. Moataz as it is a purely NLP task. 
