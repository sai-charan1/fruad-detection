# Project Architecture for Fraud Detection

## Overview

This document details the high-level architecture for our fraud detection system. The design integrates both structured and unstructured data sources to leverage a dual-model approach combining a Language Model (LLM) and a Graph Neural Network (GNN). The system is designed for scalability, modularity, and ease of deployment.

## 1. Data Collection

### Input Sources
- **Structured Data:** CSV files containing transaction details such as amount, sender/receiver info, timestamps, bank IDs, and historical fraud flags.
- **Unstructured Data:** Text-based data like transaction descriptions, invoice details, and customer complaints.

### Data Types
- **Structured Data:** Relational data that requires cleaning, normalization, and encoding.
- **Unstructured Data:** Free-text that will be processed with NLP techniques (e.g., tokenization, stop-word removal).

## 2. Data Preprocessing

### Structured Data
- **Cleaning:** Remove duplicates and handle missing values.
- **Normalization & Encoding:** Normalize numerical fields; encode categorical variables (e.g., one-hot encoding or embeddings).

### Unstructured Data
- **Text Cleaning:** Remove stop words, punctuation, and perform tokenization.
- **Embedding Extraction:** Use pre-trained models to extract text embeddings (e.g., from FinBERT).

## 3. Feature Engineering

### Embeddings & Fusion
- **Text Embeddings:** Extracted from the LLM component.
- **Relational Embeddings:** Derived from structured data processing.
- **Fusion Strategy:** Merge both embeddings (e.g., concatenation or a learned fusion layer) to form the final feature representation for each transaction.

## 4. Modeling

### LLM Component
- **Role:** Analyze text-based descriptions for fraud signals using models like FinBERT.
- **Output:** Generate text embeddings that capture semantic nuances of transaction narratives.

### GNN Component
- **Role:** Model relationships and interactions between transaction entities (e.g., sender, receiver, bank) to detect network-based fraud patterns.
- **Output:** Relational embeddings representing connectivity and potential fraud clusters.

## 5. Evaluation

### Metrics
- **Performance:** Accuracy, precision, recall, and false positive rate.
- **Visualization:** Use techniques like t-SNE or PCA to visualize clustering and data distribution.

## 6. Deployment

### API
- **Framework:** REST API built with FastAPI or Flask to serve real-time fraud predictions.
- **Endpoint:** Single endpoint that accepts new transactions, processes data through the pipeline, and returns a fraud prediction.

### Monitoring
- **Dashboards:** Real-time dashboards to monitor API performance and prediction metrics.
- **Alerts:** Configurable alerts for anomalous activity or performance issues.

## 7. Data Flow

1. **Data Ingestion:** Both structured and unstructured data are ingested into the system.
2. **Preprocessing:** Data is cleaned and transformed:
   - Structured data goes through normalization and encoding.
   - Unstructured data is tokenized and converted to embeddings.
3. **Feature Fusion:** The embeddings from both data types are fused to form a comprehensive feature vector.
4. **Modeling:** The fused data is passed to the LLM (for text) and GNN (for relational context) which work in tandem to flag potential fraud.
5. **Prediction & Evaluation:** The output is evaluated using the predefined metrics and visualizations.
6. **Deployment:** Predictions are served via a REST API, and the entire pipeline is monitored for scalability.

## 8. Scalability Considerations

- **Data Ingestion:** Use a message broker (e.g., Kafka) for real-time data ingestion.
- **Parallel Processing:** Leverage distributed computing for preprocessing and model inference.
- **Storage:** Processed data is stored under `data/processed/` with security protocols for handling sensitive financial data.
- **Resilience:** Design the API to handle spikes in data volume and ensure redundancy.

## 9. Diagram

The architecture diagram (saved as `docs/architecture/architecture_diagram.png`) visually represents the above components. It shows:
- **Data Sources:** On the left, listing both structured and unstructured data.
- **Processing Pipeline:** Center section with modules for preprocessing, feature engineering, and fusion.
- **Modeling Components:** LLM and GNN depicted interacting to produce the final fraud prediction.
- **Deployment Layer:** REST API endpoints, monitoring, and storage solutions on the right.

