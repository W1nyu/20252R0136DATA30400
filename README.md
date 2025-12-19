# Hierarchical Multi-Label Text Classification (HMTC)

**Course:** DATA304: Big Data Analysis (Fall 2025)  
**Project:** Final Project - Weakly Supervised HMTC  

## Project Overview
This project addresses the task of **Hierarchical Multi-Label Text Classification (HMTC)** under a weakly supervised setting. The goal is to classify Amazon product reviews into a hierarchical taxonomy (531 classes) **without using any labeled training data**.

We leverage class names and a taxonomy structure to generate pseudo-labels (Silver Labels) and train a supervised classifier.

### Key Methodologies

1.  **Taxonomy Enrichment:** Enhancing class representations by combining class names with related keywords.
2.  **Silver Label Generation:** Using **Sentence-BERT (`all-MiniLM-L6-v2`)** to compute semantic similarity between reviews and enriched class texts.
3.  **Supervised Training:** Fine-tuning **`bert-base-uncased`** on the generated silver labels.
4.  **Hierarchical Constraint Enforcement:** Post-processing predictions to ensure that if a child node is predicted, all its ancestor nodes are also included.

---

## Repository Structure

The code assumes the following directory structure. Please ensure the `Amazon_products` dataset is placed correctly.

```text
.
├── Amazon_products/           # Dataset directory
│   ├── train/
│   │   └── train_corpus.txt
│   ├── test/
│   │   └── test_corpus.txt
│   ├── classes.txt
│   ├── class_hierarchy.txt
│   └── class_related_keywords.txt
├── reference/                 # PDF files
│   ├── 2021.naacl-main.335.pdf
│   ├── final_project.pdf
│   └── LLM Usage.pdf
├── main.ipynb                 # Main execution notebook
├── submission.csv             
├── report.pdf                 
└── README.md

```


## File Structure and Environment
The project was implemented on an AWS SageMaker instance. To ensure reproducibility, we organized the directory as follows:

```text
/home/sagemaker-user/project_release/
|-- Amazon_products/
|   |-- train/
|   |   |-- train_corpus.txt
|   |-- test/
|   |   |-- test_corpus.txt
|   |-- classes.txt
|   |-- class_hierarchy.txt
|   |-- class_related_keywords.txt
|-- main.ipynb  (Core Implementation)
|-- submission.csv
|-- README.md
```