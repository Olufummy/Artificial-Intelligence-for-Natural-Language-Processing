## Project Summary

This project explores sentiment analysis using two neural network approaches and compares them with traditional TF-IDF baselines. The goal was to evaluate how different embedding strategies and model architectures affect performance on social media text.

Two models were implemented. The first is a BiLSTM with attention using frozen GloVe embeddings, representing static word embeddings. The second is a fine-tuned DistilBERT model, representing contextual embeddings. These were chosen to provide a clear contrast between fixed and context-aware representations.

The dataset was carefully preprocessed to preserve sentiment information while removing noise. Emojis were converted into text labels instead of being removed, URLs and user mentions were replaced with placeholders, and all text was lowercased to improve compatibility with pretrained embeddings.

For training, the dataset was split into 70% training, 15% validation, and 15% testing, with balanced class distribution. Early stopping was applied to prevent overfitting. The BiLSTM used fixed GloVe vectors, while DistilBERT was fully fine-tuned using a low learning rate.

Results showed a clear difference between the models. DistilBERT achieved the best performance with 78.6% accuracy and 0.786 F1 score, outperforming both the BiLSTM (67.4%) and the logistic regression baseline (70.7%). The BiLSTM’s lower performance was mainly due to the mismatch between GloVe’s training data and the informal language of social media, as well as its inability to adapt embeddings.

Error analysis revealed common challenges for both models. These included handling long-distance negation, sentences with mixed sentiment, sarcasm, very short texts, and informal words with different meanings. Among these, sarcasm was the most difficult to detect.

Overall, the results show that contextual models like DistilBERT are better suited for sentiment analysis, especially when working with informal text and limited data. Static embeddings remain useful for their simplicity and efficiency, but they are less effective in capturing complex language patterns.

Future improvements could include fine-tuning GloVe embeddings, using models pretrained on social media data, and increasing the dataset size to improve performance on challenging cases.
