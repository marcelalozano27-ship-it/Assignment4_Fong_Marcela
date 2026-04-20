### AI Usage Log - Assignment 4

### Fong Lieu



#### Fixing the `ipykernel` installation error

* **What task were you trying to do?**  
I was trying to install `ipykernel` so I could use my Python environment in Jupyter and run my notebook.
* **What prompt did you use?**  
I shared the terminal error showing:  
`python3.14 -m pip install ipykernel`  
and the message saying the environment was “externally managed” by `uv`.
* **What did AI suggest?**  
AI explained that the error happens because the Python installation is managed by `uv`, so I should not install packages directly using pip. It suggested creating a virtual environment and installing `ipykernel` there instead of forcing installation.
* **What did you modify?**  
I stopped trying to install directly into the system environment and switched to using a separate environment.
* **Why did you modify it?**  
Installing into a managed environment could break dependencies or cause conflicts.
* **What did you learn?**  
I learned that some Python environments are protected and require using virtual environments instead of direct installs.
* **Any AI errors found?**  
The explanation was correct, but I still had to apply it to my setup.

\---

#### Increasing support numbers and calculating support

* **What task were you trying to do?**  
I wanted to understand how to increase support values and how to calculate support in code.
* **What prompt did you use?**  
“How can I increase the support numbers”  
“can you give me code to get the support number”
* **What did AI suggest?**  
AI explained that support depends on how frequently an item or itemset appears in the dataset, and provided code to calculate support by counting occurrences and dividing by the total number of transactions.
* **What did you modify?**  
I adapted the code to match my dataset and focused on understanding support rather than trying to directly “increase” it.
* **Why did you modify it?**  
The original explanation was general, so I needed to tailor it to my specific data structure.
* **What did you learn?**  
Support is determined by the data itself and cannot be arbitrarily increased — it reflects frequency.
* **Any AI errors found?**  
No major errors.

\---

#### How to Calculate IAA in Code

* **What task were you trying to do?**  
Compute Inter-Annotator Agreement programmatically from the Label Studio export files.
* **What prompt did you use?**  
Asked AI how to calculate IAA (Cohen's Kappa and entity-level F1) from annotation exports where each document had two annotation rows, one per annotator.
* **What did AI suggest?**  
AI suggested using `sklearn.metrics.cohen\\\_kappa\\\_score` and `f1\\\_score`, converting annotations to binary token-level vectors (1 = entity, 0 = non-entity) per document and then computing scores across all overlap documents.
* **What did you modify?**  
We adapted the approach to work with character-level spans from the Label Studio JSON export rather than token-level tags, since our export stored annotations as start/end character offsets. We also used Label Studio's built-in agreement score (grouped by `annotation\\\_id`) as the primary reported metric since Kappa behaved unexpectedly on our small span set.
* **Why it was modified?**  
The AI's suggested approach assumed token-level BIO tags, but our data was stored as character span offsets. The Kappa calculation also produced a negative value due to the very small number of unique spans.
* **What was learned?**  
Cohen's Kappa can produce misleading results on small, sparse annotation sets. Label Studio's mean agreement score, computed as `df.groupby("annotation\\\_id")\\\["agreement"].first().mean()`, is a more stable metric for our setup.
* **Any AI errors found?**  
The suggested token-level Kappa approach was not directly applicable to character-offset span data.

\---

#### Evaluation Numbers Showing as 0 Despite Labeled Entities

* **What task were you trying to do?**  
Debug why precision, recall, and F1 were returning 0.0 for certain entity types even though labeled entities existed in the test set.
* **What prompt did you use?**  
Asked AI why evaluation metrics were showing as 0 when the test data clearly contained annotated entities.
* **What did AI suggest?**  
AI identified several likely causes: (1) entity label mismatches between training and test data (e.g., "PER" in training vs "PERSON" in test), (2) the model not being initialized with the correct labels before training, and (3) span misalignment caused by whitespace tokenization differences when converting from CoNLL to spaCy format.
* **What did you modify?**  
We reviewed the label normalization pipeline and confirmed that the `conll\\\_sent\\\_to\\\_spacy` conversion was correctly mapping labels, and that `ner.add\\\_label()` was called for all entity types before training. We also checked that `nlp\\\_custom.initialize()` was called after adding labels.
* **Why it was modified?**  
The root cause turned out to be that the model had very few training examples containing certain entity types, so it never learned to predict them.
* **What was learned?**  
Zero metrics can signal either a code error (label mismatch, missing initialization) or a data problem (too few examples of a class).
* **Any AI errors found?**  
AI initially assumed a label mismatch, but the actual issue was insufficient training data.

\---

#### What Parameters Are Allowed to Change to Increase F1

* **What task were you trying to do?**  
Understand which hyperparameters could be tuned to improve model F1 without changing the model structure.
* **What prompt did you use?**  
Asked AI what parameters we are allowed to change to increase F1 score in a spaCy NER model.
* **What did AI suggest?**  
AI suggested tuning epochs, dropout rate, learning rate, batch size, and train/test split, along with adding more annotated data.
* **What did you modify?**  
We kept hyperparameters the same between Model 1 and Model 2 and instead increased training data.
* **Why it was modified?**  
This allowed us to isolate the effect of data improvements on model performance.
* **What was learned?**  
More and better data has a larger impact on F1 than hyperparameter tuning in small datasets.
* **Any AI errors found?**  
None.

\---

#### Loading a CoNLL File with Space-Separated Tokens

* **What task were you trying to do?**  
Load our CoNLL annotation file into Python for training the NER model.
* **What prompt did you use?**  
Asked AI why our CoNLL file wasn’t loading correctly using the provided code, and shared our file for inspection.
* **What did AI suggest?**  
After reviewing our file, AI pointed out that our CoNLL format was space-separated rather than tab-separated, which is what the original code expected.
* **What did you modify?**  
We updated the parsing logic to split each line on whitespace instead of using a tab delimiter, and adjusted the loader accordingly.
* **Why it was modified?**  
The original code assumed standard tab-separated CoNLL format, so it failed on our file. Changing the delimiter allowed the file to be read correctly.
* **What was learned?**  
CoNLL files are not always consistently formatted, so it is important to inspect the raw data instead of assuming a standard structure.
* **Any AI errors found?**  
None — identifying the delimiter mismatch directly resolved the issue.

