# Infotex-Search-Engine-Information-Retrieval-
**Project Overview**
The Infotex Search Engine is a basic search engine developed for retrieving relevant documents from a dataset of scientific abstracts. The project was designed to demonstrate key techniques in data mining, natural language processing (NLP), and information retrieval. It incorporates well-known models such as Term Frequency-Inverse Document Frequency (TF-IDF) and relevance feedback mechanisms like query expansion.



# Dataset: Vaswani Dataset
The dataset used for this project is the Vaswani dataset, a widely used test collection in information retrieval research. It contains:
Size: Approximately 11,000 short abstracts from the field of physics.
Queries (Topics): A predefined set of queries designed to test the retrieval capabilities of information retrieval systems.
Relevance Judgments (Qrels): Relevance judgments indicate which documents are relevant to each query, providing a ground truth for evaluating retrieval effectiveness​(DSAI 201 Project Report…).



# Libraries and Tools Used
Several Python libraries were used to implement the project:

PyTerrier: A comprehensive information retrieval library used for indexing and retrieving documents, as well as for ranking.
NLTK (Natural Language Toolkit): Used for preprocessing tasks like tokenization and stopword removal.
Flask: A Python micro web framework used to create the search engine’s user interface.
Ngrok: A service used to expose the Flask application to the internet for easy access during development.


# Project Workflow
**1. Data Collection**
The Vaswani dataset was read and loaded using PyTerrier. The dataset was essential for testing and evaluating the search engine. The dataset consists of physics abstracts, which were later indexed and processed​


**2. Preprocessing**
Before indexing and retrieving documents, the text was preprocessed to standardize the data:

Tokenization: The documents were split into individual tokens or words.
Lowercasing: All text was converted to lowercase to ensure case insensitivity.
Stopword Removal: Common words like "the," "is," "and," etc., were removed using NLTK’s stopword list.
Stemming (Porter Stemmer): The words were reduced to their base form using the Porter stemming algorithm (e.g., "running" to "run").
This preprocessing step helped reduce the vocabulary size and ensure consistency in the document representation​

**3. Indexing**
Indexing was implemented to build an inverted index, which maps terms to the documents in which they appear. PyTerrier's DFIndexer was used to create this index. For each term, a posting list was created, which contains:

The document IDs where the term appears.
The frequency of each term in the respective documents​


**4. Query Processing**
Once the documents were indexed, the query processing component was developed to handle user queries:

Preprocessing of Queries: The user’s query underwent the same preprocessing steps as the documents (tokenization, lowercasing, stopword removal, and stemming).
Document Matching: PyTerrier’s TF-IDF model was employed to rank documents based on their relevance to the query. Documents that matched the query terms were retrieved from the inverted index​

**5. Query Expansion**
A key component of this project was query expansion, implemented using Relevance Feedback. The initial query was expanded using the top-ranked documents to retrieve more relevant results. The expansion was done using the RM3 method, which incorporates terms from the top-ranked documents into the original query. This significantly improved the retrieval effectiveness.

Additionally, the ELMo model was used to rerank the documents by incorporating embeddings, further improving query relevance and document ranking​.
User Interface
The user interface was created using Flask and Ngrok:

Flask: Provided a web interface for users to input queries and view results.
Ngrok: Exposed the local Flask server to the internet, allowing external users to access the search engine.
The search engine interface allows users to input a query, view the top-ranked documents, and click on document links to see their content. The interface was styled to look sleek and professional using custom HTML and CSS​




**6. User Interface**
The user interface was created using Flask and Ngrok:

Flask: Provided a web interface for users to input queries and view results.
Ngrok: Exposed the local Flask server to the internet, allowing external users to access the search engine.
Search Functionality: Users can input queries and receive top-ranked documents with clickable links to detailed content pages.
Responsive Design: The interface is styled using custom HTML and CSS to ensure a clean, professional look and compatibility across devices.
Error Handling: User-friendly feedback is provided when no results are found or if input errors occur.

The search engine interface enables users to enter a search query in the provided input field, which is then processed by the system. Based on the query, the engine retrieves and ranks the most relevant documents using techniques like TF-IDF and query expansion. The top-ranked documents are displayed in an organized list, with each document having a clickable link. When a user clicks on a link, they are directed to a detailed page that shows the document's full content, allowing for easy access and navigation through the retrieved information.


**7. Evaluation**
The search engine was evaluated based on:

Retrieval Accuracy: The relevance of the documents retrieved for various queries was measured using metrics like Precision and Recall.
Speed: The speed of document retrieval was also tested by timing the query processing and document ranking phases.
The evaluation showed that the combination of TF-IDF, query expansion, and embeddings (ELMo) significantly improved the ranking of documents for most queries​


# Techniques and Models

**1. TF-IDF (Term Frequency-Inverse Document Frequency)**
TF-IDF is a widely used term-weighting scheme in information retrieval. It measures the importance of terms in a document relative to the entire dataset:

TF: Measures how frequently a term appears in a document.
IDF: Measures how unique a term is across the entire corpus of documents.
In this project, TF-IDF was used to rank documents based on their relevance to the user’s query


**2. Query Expansion with RM3**
RM3 is a query expansion method that uses relevance feedback. The search engine analyzes the top-ranked documents for a given query and incorporates new terms (related to the query) to expand the user’s original query. This helps retrieve documents that may not contain the original query terms but are still relevant​



**3. ELMo (Embeddings from Language Models)**
ELMo is a deep contextualized word representation model. It generates embeddings (vector representations) for words based on the context in which they appear. The project used ELMo to rerank the top documents based on the similarity of their embeddings to the query. This allowed for more nuanced retrieval, especially for synonyms and related terms​


# Final Evaluation and Conclusion
The Infotex Search Engine successfully integrates multiple information retrieval techniques and models. By combining traditional TF-IDF ranking with query expansion (RM3) and embeddings (ELMo), the search engine demonstrated improved accuracy and relevance for a variety of queries. Additionally, the use of Flask and Ngrok made the system accessible to users through a user-friendly interface.

The search engine has the potential for future extensions, such as:

Supporting more complex queries.
Incorporating other advanced machine learning models for information retrieval.
Scaling the system to handle larger datasets.
Overall, the project was a success, demonstrating core concepts in data mining and information retrieval.
