Data Handling
Preprocessing:

Removed stopwords, applied lemmatization, and addressed domain-specific terminology.
Used NLTK for tokenization and processed special characters, numbers, and URLs.
Standardized text by converting it to lowercase for uniformity.
Augmentation:

Enhanced underrepresented labels through synonym replacement using WordNet.
Applied back-translation techniques to improve label balance for minority classes.
Modeling Choices
Classification Approach:

Utilized BERT-based transformer models, such as DistilBERT, for multi-label classification, leveraging their strong contextual understanding capabilities.
Fine-tuned the model with binary cross-entropy loss to accommodate multiple labels per text snippet.
Addressed class imbalance issues by implementing weighted loss functions.
Entity Extraction:

Adopted a hybrid method combining a dictionary-based lookup with a fine-tuned spaCy NER model.
Used domain_knowledge.json to identify predefined terms (e.g., competitors, features) through dictionary matching.
Tackled challenges like overlapping entities and ambiguity by prioritizing results from the spaCy NER model.
Summarization:

Employed the T5 Transformer, fine-tuned on call center-style text data, to generate concise and relevant summaries.
Effectively handled long input text by splitting it into manageable chunks before summarization.
Performance Results
Classification Metrics:

Achieved a Precision of 87%, Recall of 85%, and F1-Score of 86%.
Identified misclassification issues between labels like "Objection" and "Competition" due to similar phrasing.
Entity Extraction:

The dictionary-only method achieved a Precision of 90% and Recall of 80%.
The combined approach (dictionary + spaCy NER) improved results to a Precision of 92% and Recall of 88%.
Summarization:

ROUGE-L score: 78%, reflecting acceptable performance for the summarization task.
Error Analysis
Label Confusion: Instances of misclassification, such as between "Pricing Discussion" and "Objection," due to overlapping terms like "cheaper" and "discount."
Entity Detection Gaps: Certain entities were missed when the phrasing deviated significantly from entries in the dictionary.
