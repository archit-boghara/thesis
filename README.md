# Description

This Python script implements and evaluates retrieval models on the **Cranfield dataset**, focusing on both baseline and hybrid information retrieval techniques. The goal is to compare the performance of different retrieval approaches and understand the impact of combining sparse and dense retrieval methods.

**Key Components:**

- **Dataset Loading:**
  - Utilizes `ir_datasets` to load the Cranfield dataset, which consists of 1,400 documents and 225 queries.
  - Prepares documents, queries, and relevance judgments for retrieval and evaluation.

- **Baseline Retrieval Models:**
  - **BM25 (Sparse Retrieval Baseline):**
    - Indexes documents using Pyserini's BM25 implementation.
    - Retrieves documents based on term frequency and inverse document frequency.
  - **Dense Retrieval Baseline:**
    - Uses a pre-trained BERT-based model (`sentence-transformers/all-MiniLM-L6-v2`) to encode documents and queries into dense vector embeddings.
    - Performs retrieval using cosine similarity between query and document embeddings.

- **Hybrid Retrieval Techniques:**
  - **Hybrid COIL-like Retrieval:**
    - Combines BM25 scores with dense retrieval scores using a weighted sum.
    - Simulates the COIL (Contextualized Inverted List) approach by integrating term-based and contextual representations.
  - **Hybrid Blended RAG-like Retrieval:**
    - Retrieves candidate documents using BM25.
    - Re-ranks the candidates using dense embeddings, inspired by the Blended Retrieval-Augmented Generation (RAG) method.

- **Evaluation:**
  - Calculates **Precision@10** for each retrieval method.
  - Compares the number of relevant documents retrieved in the top 10 results across all queries.
  - Outputs the average precision scores for each model.

# Research Questions Addressed

**1. How does the integration of sparse and dense retrieval methods affect retrieval performance on the Cranfield dataset?**

- **Explanation:**
  - The script compares the performance of baseline models (BM25 and dense retrieval) with hybrid models that combine both approaches.
  - By evaluating the **Precision@10** metric, it assesses whether hybrid methods can retrieve more relevant documents than the individual baselines.
  - The results indicate the effectiveness of combining term-based and contextual information in improving retrieval accuracy.

**2. Can simple hybrid retrieval techniques inspired by COIL and Blended RAG provide performance gains over traditional retrieval models in small-scale information retrieval tasks?**

- **Explanation:**
  - The hybrid retrieval methods implemented are simplified versions inspired by COIL and Blended RAG principles.
    - **Hybrid COIL-like Retrieval** combines scores from BM25 and dense embeddings.
    - **Hybrid Blended RAG-like Retrieval** uses BM25 for initial retrieval and dense embeddings for re-ranking.
  - The script evaluates whether these straightforward hybrid approaches can outperform the traditional BM25 and dense retrieval models.
  - This addresses the feasibility and benefits of applying hybrid techniques in a simplified context suitable for a bachelor's thesis.

# How to Use the Script

**Prerequisites:**

- Install the required Python packages:

  ```bash
  pip install ir_datasets pyserini sentence-transformers tqdm
  ```

**Running the Script:**

1. Save the script to a file, e.g., `hybrid_retrieval.py`.

2. Run the script using the command:

   ```bash
   python hybrid_retrieval.py
   ```

**Interpreting the Results:**

- The script will output the Precision@10 for each retrieval method:

  ```
  Retrieval Performance (Precision@10):
  BM25 Baseline: 0.XXXX
  Dense Retrieval Baseline: 0.YYYY
  Hybrid COIL-like Retrieval: 0.ZZZZ
  Hybrid Blended RAG-like Retrieval: 0.WWWW
  ```

- **Analysis:**
  - Compare the precision values to determine which retrieval method performs best.
  - Higher Precision@10 indicates that the model retrieves more relevant documents in the top 10 results.
  - Evaluate whether hybrid methods offer improvements over the baselines.

# Conclusion

This script demonstrates the implementation and evaluation of baseline and hybrid retrieval models on the Cranfield dataset. By addressing the research questions, it provides insights into:

- The effectiveness of combining sparse and dense retrieval methods.
- The potential performance gains from simple hybrid approaches inspired by advanced models like COIL and Blended RAG.

**Note:** The hybrid methods are simplified for the purpose of this project, making them suitable for a bachelor's thesis while still offering valuable findings in the field of information retrieval.

# References

- **Cranfield Dataset:** A foundational dataset in information retrieval research, consisting of scientific abstracts and queries.
- **Pyserini:** An information retrieval toolkit that provides support for BM25 and integration with dense retrieval models.
- **SentenceTransformers:** A library for computing dense vector representations of sentences and paragraphs using pre-trained models.

# Acknowledgments

- **ir_datasets:** For providing easy access to the Cranfield dataset.
- **Developers of Pyserini and SentenceTransformers:** For creating tools that simplify the implementation of retrieval models.

---
