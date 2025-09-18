# Auto Correct Model

In our case, the autocorrection system needs to be **word-based and efficient** because the text is generated letter by letter from EEG signals. A word-level correction avoids the complexity of context-dependent models and provides fast, lightweight corrections that can run in real time. Since the system is meant to support individuals with severe disabilities, efficiency is crucial—delays or heavy models would make communication slow and impractical. Therefore, choosing a correction approach that balances **accuracy with real-time performance** is essential:contentReference[oaicite:0]{index=0}.  

---

## Comparison of Commonly Used Models

| Library        | Efficiency (Speed) | Accuracy (Word-Level) | Notes                                                                 |
|----------------|--------------------|------------------------|----------------------------------------------------------------------|
| autocorrect    | 7/10               | 6/10                   | Very lightweight, quick setup, good for simple corrections.          |
| pyspellchecker | 8/10               | 7/10                   | Pure Python, widely used, balanced between speed and accuracy.       |
| SymSpell       | 10/10              | 8/10                   | Extremely fast & memory-efficient, great for real-time use.          |
| Hunspell       | 6/10               | 9/10                   | Industry-grade, robust with morphology/affixes, but heavier.         |
| JamSpell       | 8/10               | 8/10                   | Statistical model, accurate at sentence-level, efficient enough.     |
