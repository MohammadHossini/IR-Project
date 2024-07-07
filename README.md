# IR-Project

![image](https://github.com/MohammadHossini/IR-Project/assets/106095825/54615004-0839-47a1-8a29-e7f43bfd2e0c)



---

# Document Processing and Ranking System

This project is a comprehensive document processing and ranking system that reads a set of documents, processes them to create a dictionary of terms, and computes TF-IDF values for these terms. It also allows users to enter queries, rank documents based on cosine similarity to the query, and rerank selected documents. The results are output to Excel files for further analysis.

## Overview

The script performs the following steps:

1. **Read and preprocess documents**: It reads documents from a file, processes each document to remove stopwords, stems words, and creates a dictionary of terms.
2. **Calculate TF-IDF values**: It computes Term Frequency (TF), Inverse Document Frequency (IDF), and TF-IDF values for the terms in the documents.
3. **Query processing and ranking**: It allows users to enter a query, processes the query, and ranks the documents based on cosine similarity to the query.
4. **Reranking**: Users can select specific documents to rerank based on the updated TF-IDF values after considering the selected documents.

## Dependencies

- `nltk`
- `numpy`
- `pandas`
- `tkinter`

Ensure you have these packages installed before running the script.

## Formulas

### Term Frequency (TF)

## ${TF}(t, d) = 1 + \log_{10}(f(t, d)) $ ## 

where f(t, d) is the frequency of term \( t \) in document \( d \).

### Inverse Document Frequency (IDF)

## ${IDF}(t) = \log_{10}\left(\frac{N}{n(t)}\right) $ ##

where \( N \) is the total number of documents, and n(t) is the number of documents containing term \( t \).

### TF-IDF

## ${TF-IDF}(t, d) = \text{TF}(t, d) \times \text{IDF}(t)$ ##

### Cosine Similarity

## $cos(\theta) = \frac{\vec{A} \cdot \vec{B}}{\|\vec{A}\| \|\vec{B}\|}$ ##

where A and B are the TF-IDF vectors of the query and the document respectively.

## Script Explanation

### Data Preparation and Preprocessing

1. **Loading Documents**: The `select_file()` function loads a dataset of documents from a file named `cran.all.1400`.

2. **Processing Documents**: 
    - The `process_document()` function converts each document into a list of words, filters out stopwords, stems the words, and creates a dictionary of unique terms.
    - The documents are then saved as individual text files.

3. **Creating the Dictionary**: A dictionary of stemmed words is created and saved to an Excel file `dictionary.xlsx`.

### TF-IDF Calculation

1. **Term Frequency (TF)**: The `calculate_term_frequency()` function calculates the frequency of each term in each document.

2. **Document Frequency (DF)**: The `calculate_document_frequency()` function calculates the number of documents containing each term.

3. **TF and IDF Arrays**: The script initializes and populates `tf_array` and `idf_array` for storing TF and IDF values respectively.

4. **TF-IDF Calculation**: The TF-IDF values are computed and stored in `tf_idf_array`.

### Query Processing and Ranking

1. **Query Input**: The `take_query_from_user()` function takes a query input from the user, processes the query similarly to how the documents were processed, and calculates the TF-IDF vector for the query.

2. **Cosine Similarity Calculation**: The `calculate_cosine()` function calculates the cosine similarity between the query TF-IDF vector and each document TF-IDF vector.

3. **Ranking Documents**: The `rank_cosine()` function ranks the documents based on their cosine similarity to the query and outputs the results to an Excel file `cosine_similarity_rank.xlsx`.

### Reranking

1. **Selecting Documents**: The `choose()` function allows the user to select specific documents for reranking.

2. **Reranking**: The `rerank()` function updates the query TF-IDF vector based on the selected documents and reranks the documents accordingly, outputting the results to an Excel file `cosine_similarity_rerank.xlsx`.

## Running the Script

1. **Initial Setup**: Ensure you have the necessary dependencies installed.

2. **Executing the Script**: Run the script. A GUI will appear allowing you to enter a query and rerank documents.

3. **Results**: The results of the TF, IDF, TF-IDF calculations, and document rankings will be saved as Excel files for further analysis.

## Conclusion

This project provides a robust framework for document processing and ranking based on TF-IDF and cosine similarity. It allows for efficient querying and reranking of documents, making it a valuable tool for information retrieval tasks.

