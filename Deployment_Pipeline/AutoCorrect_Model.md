# Auto Correct Model

In our case, the autocorrection system needs to be **word-based and efficient** because the text is generated letter by letter from EEG signals. A word-level correction avoids the complexity of context-dependent models and provides fast, lightweight corrections that can run in real time. Since the system is meant to support individuals with severe disabilities, efficiency is crucial—delays or heavy models would make communication slow and impractical. Therefore, choosing a correction approach that balances **accuracy with real-time performance** is essential.

---

## Initial Comparison of Commonly Used Models 

| Library                     | Efficiency (Speed) | Accuracy (Word-Level) | Notes                                                                 |
|-----------------------------|--------------------|------------------------|----------------------------------------------------------------------|
| autocorrect                 | 7/10               | 6/10                   | Very lightweight, quick setup, good for simple corrections.          |
| pyspellchecker              | 8/10               | 7/10                   | Pure Python, widely used, balanced between speed and accuracy.       |
| SymSpell                    | 10/10              | 8/10                   | Extremely fast & memory-efficient, great for real-time use.          |
| Hunspell (via spylls)       | 6/10               | 9/10                   | Industry-grade, robust with morphology/affixes, but heavier.         |
| SymSpell + Left-to-Right    | 9/10               | 5/10                   | Context-aware using past words only, lightweight but less accurate.  |


# Evaluation of Word-Based Autocorrection Models

We drafted and tested code for **five different autocorrection models** under multiple circumstances to better understand their trade-offs between **speed** and **accuracy**. The models tested were:

- **Autocorrect (Python library)**
- **PySpellChecker**
- **SymSpell (basic)**
- **Hunspell (via spylls, pure-Python)**
- **SymSpell + Left-to-Right Context (past-only)**

Each model was benchmarked on three tasks:
1. **Small corpus** – A shorter paragraph with spelling mistakes.
2. **Large corpus** – A longer paragraph with more errors and complexity.
3. **Misspelled-words only** – Accuracy measured only on words that were originally incorrect.

---

## 1. Small Corpus

We first tested the models on a **shorter paragraph** containing spelling mistakes. Accuracy was calculated across the **entire corpus**.

**Misspelled Corpus:**
```

Tday I went to the schoul to met with my freinds and discuus the projct.
We had planed to start earliy, but evryone arived late becuase of the trafic.
The libary was to noisy, so we moved to a quet classrom.
I wrote sevral paragraps explaing our ideea, but there were many speling mistaks.
At lunch, we at sandwhiches and drank cofee while we reviewd the requirments.
Eventualy, we agredd to updat the timline and asign cleer responsibilites to each person.
Tomorow, I will send the summery with the corect verion and confirm the scheduel with the instrutor.

```

**Correct Corpus:**
```

Today I went to the school to meet with my friends and discuss the project.
We had planned to start early, but everyone arrived late because of the traffic.
The library was too noisy, so we moved to a quiet classroom.
I wrote several paragraphs explaining our idea, but there were many spelling mistakes.
At lunch, we ate sandwiches and drank coffee while we reviewed the requirements.
Eventually, we agreed to update the timeline and assign clear responsibilities to each person.
Tomorrow, I will send the summary with the correct version and confirm the schedule with the instructor.

```

**Results:**

| Model                        | Avg Time/Word | Word Accuracy |
|------------------------------|---------------|---------------|
| Autocorrect (Python library) | 0.115 ms/word | 82.7%         |
| PySpellChecker               | 1.037 ms/word | 88.8%         |
| SymSpell (basic)             | 0.033 ms/word | 82.7%         |
| Hunspell (spylls)            | 4.500 ms/word | 83.7%         |
| SymSpell + Left-to-Right     | 0.528 ms/word | 59.2%         |

---

## 2. Large Corpus

Next, we used a **longer paragraph** with more errors, evaluating accuracy across the **entire corpus**.

**Misspelled Corpus:**
```

Yesturday mornng, I desided to wake up earli and take a quick walke to the libary,
but the weathr was unpredicteble and it strated to rain hevily. On my way, I met two freinds
who were also planing to study, yet we all relized we had fogoten our noteboks and pencials.
At the coffe shop nerby, we ordred sandwitches and capachinos, but the barrista misspeled my
name on the cup as Alxenderr, which made us laught for a whiel. When we finaly arived at the
libary, it was overcrowded and very noizy, so we searched for a quiter clasroom in the oldr
building. I began writting a draft of our reseach propasal, explaing the metodolgy and the
expreimental desgin, but I kept makng speling mistkes becuse I was in a hurry. My freinds
sugested we take a brek and reorgnize the timline, asign clerer resposnibilites, and setup
a sharedd calender. Tomorow, we inted to meet agan with the instrutor to reveiw the feedbak,
corect the erors, and submitt the finel versoin befor the dedline at midnigt.

```

**Correct Corpus:**
```

Yesterday morning, I decided to wake up early and take a quick walk to the library,
but the weather was unpredictable and it started to rain heavily. On my way, I met two friends
who were also planning to study, yet we all realized we had forgotten our notebooks and pencils.
At the coffee shop nearby, we ordered sandwiches and cappuccinos, but the barista misspelled my
name on the cup as Alexander, which made us laugh for a while. When we finally arrived at the
library, it was overcrowded and very noisy, so we searched for a quieter classroom in the older
building. I began writing a draft of our research proposal, explaining the methodology and the
experimental design, but I kept making spelling mistakes because I was in a hurry. My friends
suggested we take a break and reorganize the timeline, assign clearer responsibilities, and set up
a shared calendar. Tomorrow, we intend to meet again with the instructor to review the feedback,
correct the errors, and submit the final version before the deadline at midnight.

```

**Results:**

| Model                        | Avg Time/Word | Word Accuracy |
|------------------------------|---------------|---------------|
| Autocorrect (Python library) | 0.047 ms/word | 72.3%         |
| PySpellChecker               | 33.263 ms/word| 76.8%         |
| SymSpell (basic)             | 0.036 ms/word | 72.3%         |
| Hunspell (spylls)            | 5.543 ms/word | 72.9%         |
| SymSpell + Left-to-Right     | 0.052 ms/word | 52.5%         |

---

## 3. Focusing on Misspelled Words

Finally, we measured **accuracy only on originally misspelled words**, to see how well each model actually corrected errors instead of benefiting from already correct words.

**Misspelled Corpus:**
```

I tolld my frend how are you afer we went to scool.
I didnt recieve your emial yesturday, can you resent it agan?
We are going to the libary later to finsh our homwork.
The wethar was relly nice so we walkd to the coffe shop nearbly.
She said she wil call me tomorow morning befor class.
I bought vegtables and bred from the grocry store on my way home.
Please chekc the sheduele and let me no if your free on Thusday.
After luch we met the instrutor to discus the projeckt detales.
He allways forgets his pasword and needs to resset it evry weak.
Thanks for your help, I appriciate your quick responce.

```

**Correct Corpus:**
```

I told my friend how are you after we went to school.
I didn’t receive your email yesterday, can you resend it again?
We are going to the library later to finish our homework.
The weather was really nice so we walked to the coffee shop nearby.
She said she will call me tomorrow morning before class.
I bought vegetables and bread from the grocery store on my way home.
Please check the schedule and let me know if you’re free on Thursday.
After lunch we met the instructor to discuss the project details.
He always forgets his password and needs to reset it every week.
Thanks for your help, I appreciate your quick response.

```

**Results:**

| Model                        | Avg Time/Misspelled Word | Accuracy (Misspelled Only) |
|------------------------------|---------------------------|-----------------------------|
| Autocorrect (Python library) | 0.271 ms/misspelled-word | 65.9%                      |
| PySpellChecker               | 33.137 ms/misspelled-word| 73.2%                      |
| SymSpell (basic)             | 0.075 ms/misspelled-word | 65.9%                      |
| Hunspell (spylls)            | 12.449 ms/misspelled-word| 48.8%                      |
| SymSpell + Left-to-Right     | 0.147 ms/misspelled-word | 9.8%                       |

---

## Conclusion

Our experiments show clear **trade-offs** between efficiency and accuracy:

- **SymSpell (basic)** is by far the **fastest**, achieving corrections in fractions of a millisecond per word, but its accuracy remains modest (≈72–83%).  
- **PySpellChecker** consistently achieved the **highest accuracy (≈73–89%)**, but at the cost of very **high latency** on larger corpora.  
- **Hunspell** provides strong morphological support but is relatively **slow** and its accuracy was not consistently higher than simpler models.  
- **Autocorrect (Python library)** is lightweight and reasonably accurate, making it a **balanced choice for small-scale tasks**.  
- **SymSpell + Left-to-Right Context**, despite the idea of using past words only, performed **poorly on accuracy**, suggesting that a more robust language model (e.g., KenLM or a pretrained n-gram LM) would be needed for context to pay off.

Overall, for **real-time applications** where **speed is critical**, **SymSpell** is the most practical. For scenarios where **accuracy is more important** than latency, **PySpellChecker** is preferable. To improve context-aware correction, integrating a **proper language model** with SymSpell candidates would likely yield the best of both worlds.

📓 The full notebook with code for each model and its testing results can be accessed here: [Colab Notebook](https://colab.research.google.com/drive/1lEITvAL1paxqF4sKESisg458r4AfPGrR?usp=sharing)
```

