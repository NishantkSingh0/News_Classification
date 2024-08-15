# News Classification Using Parallel Transformer Encoders
This project focuses on classifying news articles using a customized model based on the Transformer architecture. The architecture is designed to process and combine information from both the title and description of news articles, enabling high accuracy in classification.

## 1. Dataset:
### [AG News](https://www.kaggle.com/datasets/amananandrai/ag-news-classification-dataset)
The dataset used in this project is the AG News dataset, a widely used benchmark dataset for text classification. The dataset contains four classes representing different news topics:

i. _World_  
ii. _Sports_  
iii. _Business_  
iv. _Sci/Tech_  
  
Each entry in the dataset includes both a title and a description of the news article. For this project, I selected the first 15,000 rows from the dataset to train the model.

### ___Data Preprocessing___
The text data (both title and description) was preprocessed to ensure consistency and to facilitate efficient training. The preprocessing steps included padding, tokenization, and embedding, along with the incorporation of positional encodings to preserve the order of words.

## 2. Model Architecture:
The architecture is built around the Transformer encoder, with a key feature being the parallel processing of the title and description using separate encoders.

### ___Architecture Overview___
Dual Encoder Structure: The model employs two parallel encoder blocks:
  #### __Encoder 1:__ Processes the Description of the news article.
  #### __Encoder 2:__ Processes the Title of the news article.
Embedding and Positional Encoding: Both Title and Description inputs undergo tokenization, padding, embedding, and positional encoding before being fed into their respective encoders.

### Attention and Feed-Forward Network: Each encoder block is composed of:

Multi-Head Self-Attention layers to capture relationships between tokens.   
Feed-Forward Neural Networks (FFN) with Add & Norm layers to enhance the learned representations.   
Concatenation and Global Pooling: The outputs from both encoders are concatenated and passed through a global max pooling layer, followed by a fully connected layer.   

### Classification: The final dense layer outputs predictions across the four classes.

![Screenshot (126)](https://github.com/user-attachments/assets/02e52102-2872-49c5-b2db-e6334ad12bc2)


# 3. Model Working:
The model works by independently extracting patterns from both the Title and Description of a news article. The self-attention mechanism within each encoder block enables the model to understand contextual information by focusing on relevant parts of the input. By processing both the title and description simultaneously, the model gains a richer representation of the content, allowing for more accurate classification.

Once the outputs from both encoders are obtained, they are pooled, concatenated, and passed through a dense layer to predict the news category.

### Key Steps:
#### i. Input: Title and Description are tokenized and padded.
#### ii. Embedding & Positional Encoding: Both inputs are converted into fixed-size embeddings, with positional encodings added.
#### iii. Parallel Encoding: The Title and Description pass through their respective encoder blocks.
#### iv. Concatenation & Pooling: Outputs from both encoders are concatenated and globally pooled.
#### v. Classification: The pooled vector is passed through a dense layer to generate predictions.
  
# 4. Complexity of Dataset:
The AG News dataset, while popular, presents challenges due to its brevity in the title and diversity in the description. The dataset’s complexity lies in the nuanced distinctions between the four classes, especially when only a small portion of the data is used, as done in this project (15,000 samples).

By leveraging parallel encoders, the model effectively mitigates these challenges by combining the broader context from the description with the focused keywords from the title.

# 5. Overview:
This project demonstrates a novel approach to text classification using parallel Transformer encoders. By processing both the title and description of a news article separately and then combining their outputs, the model achieves impressive performance, attaining an accuracy of 99.6% on the test set. The combination of attention mechanisms and feed-forward layers allows for a deep understanding of the input data, making this architecture particularly effective for tasks that require nuanced contextual comprehension.

# Key Achievements:
### i. __High Accuracy:__ Achieved 99.6% accuracy using only 15,000 samples from the AG News dataset.
### ii. __Innovative Architecture:__ The dual-encoder setup captures a richer representation of the data by leveraging both title and description.
### iii. __Scalability:__ The architecture can be extended to other classification tasks with similar data structures.
