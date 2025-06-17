## NLP-Project

## Detecting COVID-19 Misinformation Using NLP & Transformer Models
From the earliest days of the pandemic, false or misleading claims about COVID-19 ranging from miracle cures to vaccine conspiracies have proliferated across news sites and social media, undermining public health efforts and eroding trust. In this capstone project, we develop and evaluate a robust, end-to-end Natural Language Processing pipeline for automatically detecting COVID-19 misinformation in both news articles and social media posts. Leveraging two state-of-the-art transformer architectures—RoBERTa and Llama-3.2-1B-Instruct we fine-tune models on the CoAID dataset, which contains 726 verified “reliable” articles and 39 confirmed “misinformation” samples. To address the severe class imbalance, we apply class-weighting in the loss function alongside RandomOverSampler augmentation, producing a balanced training set of 432 documents.

### Key steps in the pipeline:

### Data Collection & Preprocessing

Ingest the CoAID dataset of COVID-19 news and social posts.

Clean and normalize text by stripping punctuation, URLs, and stopwords, and apply lemmatization to reduce inflectional forms.

Perform sentiment analysis to capture emotional tone, since misinformation often carries charged language.

Model Training & Fine-Tuning

RoBERTa: Fine-tuned for three epochs using a 512-token input window, a learning rate of 2×10⁻⁵, and batch size of 8.

Llama-3.2-1B: Evaluated in both zero-shot prompting and supervised fine-tuning modes (learning rate 3×10⁻⁴, batch size 16, 3–4 epochs).

Integrated class weights (0.52 for reliable, 9.2 for misinformation) into cross-entropy loss to penalize minority-class misclassifications.

### Evaluation & Robustness Checks

Measured standard classification metrics (accuracy, precision, recall, F1-score) and plotted AUC-ROC curves.

RoBERTa achieved an overall accuracy of 96.75%, with an F1-score of 70.5% on the misinformation class and 98.3% on the reliable class.

Llama (fine-tuned) reached 98% accuracy and an F1-score of 0.97, outperforming RoBERTa. Even in a zero-shot setting, Llama achieved 82% accuracy (F1 = 0.90).

Employed bootstrapping (1,000 iterations) to confirm metric stability and narrow confidence intervals.

### Insights & Contributions

Demonstrated transformer-based models’ effectiveness for public health informatics, enabling rapid, scalable identification of harmful COVID-19 misinformation.

Showcased practical techniques for mitigating class imbalance in real-world datasets.

Produced an open-source framework (preprocessing scripts, model training notebooks, evaluation dashboards) for researchers and practitioners to adapt to future “infodemics.”

This project underscores how advanced NLP and large language models can play a critical role in safeguarding public trust and supporting evidence-based health communication. The code, trained model checkpoints, and detailed methodology are available in this repository for reproducibility and further extension into multilingual or multimodal misinformation detection.
