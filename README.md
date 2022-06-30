# Name Entity Recognition using Deep learning and transfer learning methods

In this notebook we created several name entity recognition models to identitfy technical terms referring to concepts of interest to biologists in the domain of molecular biology.
Terms and their classification:  
'O': 0, 'B-protein': 1, 'I-protein': 2, 'B-cell_type': 3, 'I-cell_type': 4, 'B-cell_line': 5, 'I-cell_line': 6, 'B-DNA': 7, 'I-DNA': 8, 'B-RNA': 9, 'I-RNA': 10

The data set we use to train the models is the JNLPBA dataset:

Dataset from: https://huggingface.co/datasets/EMBO/BLURB

Dataset name: "EMBO/BLURB", "JNLPBA"

Article: https://aclanthology.org/W04-1213/

JNLPBA

The BioNLP / JNLPBA Shared Task 2004 involves the identification and classification of technical terms referring to concepts of interest to biologists in the domain of molecular biology. The task was organized by GENIA Project based on the annotations of the GENIA Term corpus (version 3.02). Corpus format: The JNLPBA corpus is distributed in IOB format, with each line containing a single token and its tag, separated by a tab character. Sentences are separated by blank lines.

## Results
![image](https://user-images.githubusercontent.com/62335786/176397231-8b73ead5-93b0-45fe-998c-d2851d7a5e99.png)  
Transfer learning model:  
![image](https://user-images.githubusercontent.com/62335786/176397679-1ca8f994-f63c-4934-b1c1-bfd8fc7bc321.png)


As expected, all of the bidirectional models performed better than the single direction models.
Although the bidirectional LSTM is the best performing model with a F1 score of 0.7802, the BRNN and BGRU models are achieving similar results (0.769 and 0.771 F1 scores). This can indicate that the influence of the long term memory on our data is not significant.
Similar results are also achieved using the transfer learning model (F1 0.69).

**RNN models**  
All RNN models show the best performance within the first 8 to 15 epochs. From the loss graphs we can see that after reaching this point the models are starting to over fit the data to the training data (train loss is decressing and validation loss is increasing).

**Transfer learning model**  
When inspecting the transfer learning model resaults in grater details we can see that the model performance on the "cell_line" class, which is the second smaller class is lacking behind. Rebalanceing of the classes might help in improving our results.  

Tools: python including pytorch and Hugging Face transformers package
