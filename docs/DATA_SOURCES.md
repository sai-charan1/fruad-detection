# Data Sources & Requirements

## 1. Structured Data Sources

### Transaction Details
- **Description:** Contains transaction amounts, sender and receiver details, timestamps, bank IDs, and historical fraud flags.
- **Data Repositories:**
  - **Kaggle:**
    - [IEEE-CIS Fraud Detection Dataset](https://www.kaggle.com/c/ieee-fraud-detection) – A comprehensive dataset with various transaction details and fraud indicators.
    - [Credit Card Fraud Detection Dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud) – Contains credit card transaction records with fraud labels.
  - **UCI Machine Learning Repository:**
    - [Credit Card Fraud Detection](https://archive.ics.uci.edu/ml/datasets/credit+card+fraud) – Dataset with anonymized transaction data.

## 2. Unstructured Data Sources

### Text Data
- **Description:** Includes transaction descriptions, invoice details, and customer complaint logs.
- **Data Acquisition Methods:**
  - **Internal Systems:** Extract from logs, invoice management systems, and customer feedback.
  - **Web Scraping/APIs:** Use libraries such as BeautifulSoup or Scrapy to scrape publicly available transaction narratives or customer reviews (ensure compliance with website policies).
  - **APIs:** Identify potential APIs that offer business or financial news which might contain relevant text data (document API keys and access details as needed).

## 3. Data Requirements

### Structured Data Requirements
- **Essential Fields:**
  - **Transaction Amount**
  - **Sender/Receiver IDs**
  - **Timestamp**
  - **Bank ID**
  - **Fraud Flag (Historical)**
  
### Unstructured Data Requirements
- **Essential Fields:**
  - **Transaction Notes/Descriptions**
  - **Invoice Details**
  - **Customer Feedback/Complaints**

## 4. Integration & Storage

- **Processed Data Storage:**
  - **Location:** Store all processed data under `data/processed/`.
  - **Considerations:** Ensure proper data security and compliance, especially for sensitive financial information.

- **Documentation:**
  - Each data source entry includes URLs, a brief description, and any data preparation notes.
