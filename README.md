Report: Text Processing and Information Retrieval System
Introduction
In this report, I present the methodology and steps taken to develop a text processing and information retrieval system. The objective of this project was to preprocess a large dataset of Wikipedia articles, perform various text processing tasks such as tokenization, stopword removal, and lemmatization, and then build an information retrieval system capable of efficiently retrieving relevant documents based on user queries.

Dataset
The dataset used for this project consists of Wikipedia articles stored in a CSV file format. The file contains a large collection of articles, each represented as a single row in the CSV file.

Methodology
1. Data Preprocessing
Read Data: The Wikipedia dataset was read from the provided CSV file using the data_preprocessing.py script.
Basic Cleaning: Basic cleaning tasks such as removing HTML tags, punctuation, and special characters were performed on the text data.
Tokenization: The text was tokenized into individual words.
Stopword Removal: Stopwords were removed from the text to reduce noise.
Lemmatization: Words were lemmatized to convert them to their base form.
Output: The preprocessed data was saved to a new CSV file.
2. Word Enumeration MapReduce Job
Mapper: The word_enumeration_mapper.py script tokenized the text and emitted (word, 1) pairs.
Reducer: The word_enumeration_reducer.py script summed up the counts for each word and emitted (word, total_count) pairs.
Output: The vocabulary with word IDs was saved to a file.
3. Document Count MapReduce Job
Mapper: The document_count_mapper.py script tokenized each document, emitted (word, 1) pairs, and document IDs.
Reducer: The document_count_reducer.py script counted the number of documents each word appears in and emitted (word, document_count) pairs.
Output: IDF values for each word were saved to a file.
4. Indexer MapReduce Job
Mapper: The indexer_mapper.py script tokenized each document and emitted (word, (document_id, term_frequency)) pairs.
Reducer: The indexer_reducer.py script calculated TF/IDF weights for each word-document pair and emitted (document_id, sparse_vector) pairs.
Output: The index with document IDs and their TF/IDF vectors was saved to a file.
5. Query Processor
Input: The query_processor.py script accepted user queries.
Vectorization: User queries were converted into TF/IDF vectors using the IDF values computed earlier.
Similarity Calculation: Cosine similarity between the query vector and document vectors was computed.
Output: Relevant documents sorted by similarity scores were returned.
6. Testing
Local Testing: Each module was tested locally on a smaller dataset for faster development.
Integration Testing: The entire system was tested on a subset of the dataset before running on the full dataset.
7. Documentation and Finalization
Documentation: Detailed documentation for each module's functionality, input/output, and usage was written.
Finalization: The project was finalized, and all scripts and documentation were reviewed for completeness and accuracy.
Conclusion
In conclusion, this project successfully implemented a text processing and information retrieval system using Hadoop MapReduce and Python. The system is capable of preprocessing large datasets, building vocabulary, calculating TF/IDF values, indexing documents, and efficiently retrieving relevant documents based on user queries. The modular design and thorough testing ensure the reliability and scalability of the system for handling large-scale text data.
