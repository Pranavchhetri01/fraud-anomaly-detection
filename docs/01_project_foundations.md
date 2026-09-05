# Phase 1: Project Foundations

## 1.1 Business Problem Definition

### Project Scenario

This project assumes that we are working as data scientists for a fictional digital-payment company.

The company processes many financial transactions, including payments, transfers, withdrawals and deposits. Because the number of transactions is too large for employees to inspect manually, the company needs an automated system that can identify potentially fraudulent activity.

The system will examine transactions, calculate fraud-risk scores and flag suspicious transactions for further investigation.

### Business Problem

Some transactions processed by the company may be fraudulent. Undetected fraud can cause financial loss, increase investigation costs and damage customer trust.

However, incorrectly flagging legitimate transactions can also create problems. Genuine payments may be delayed or blocked, customers may become frustrated and investigators may receive unnecessary alerts.

Therefore, the company needs a fraud-detection system that identifies as much fraudulent activity as possible while limiting the number of legitimate transactions incorrectly flagged.

### Project Objective

The objective of this project is to develop and compare supervised fraud-detection models and unsupervised anomaly-detection models.

The final system should:

- Assign a fraud-risk score to each transaction.
- Identify potentially fraudulent transactions.
- Detect unusual transaction patterns.
- Limit unnecessary alerts involving legitimate customers.
- Support investigators rather than automatically making every final decision.
- Explain why transactions receive high-risk scores.

### Machine-Learning Output

For supervised fraud detection, each transaction belongs to one of two classes:

- `0`: legitimate transaction
- `1`: fraudulent transaction

The model may also produce a fraud probability between `0` and `1`.

For example:

- `0.10`: relatively low estimated fraud risk
- `0.65`: moderate estimated fraud risk
- `0.95`: relatively high estimated fraud risk

A decision threshold will later be selected to determine which transactions should be flagged for investigation.

### Fraud Detection and Anomaly Detection

A supervised fraud-detection model learns from historical transactions that already have known fraud labels.

An unsupervised anomaly-detection model is not shown fraud labels during training. Instead, it learns patterns in transaction data and identifies observations that are unusually different.

An anomalous transaction is not automatically fraudulent. It may represent unusual but legitimate customer behaviour.

### Stakeholders

The main stakeholders are:

- Customers using the payment service
- Fraud investigators
- The company's fraud and risk teams
- Data scientists and engineers
- Company management
- Regulatory and compliance teams

### Types of Prediction Errors

A **false positive** occurs when a legitimate transaction is incorrectly flagged as fraudulent.

Possible consequences include:

- Blocking a genuine payment
- Frustrating a customer
- Increasing investigation costs

A **false negative** occurs when a fraudulent transaction is incorrectly classified as legitimate.

Possible consequences include:

- Financial loss
- Missed fraudulent activity
- Reduced customer trust

The final model must balance these two types of errors according to the company's risks and investigation capacity.

### Initial Problem Statement

> A digital-payment company processes a large number of daily transactions that cannot all be inspected manually. The company requires a system that assigns fraud-risk scores to transactions and flags suspicious activity for investigation. This project will develop and compare supervised fraud-detection and unsupervised anomaly-detection models while considering class imbalance, false alarms, missed fraud, explainability and business costs.

## 1.2 Machine-Learning Problem Formulation

### Unit of Observation

The unit of observation is an individual financial transaction. Each row of the dataset represents one transaction, and the system will generate a risk assessment for each transaction.

### Input Features

The model inputs are represented by `X`. These may include transaction amount, transaction type, sender balance, recipient balance and engineered behavioural features.

Only information available when the transaction occurs should be used for prediction. Using information created after the fraud outcome becomes known could cause data leakage.

### Target Variable

The supervised model's target variable is represented by `y`.

- `0`: legitimate transaction
- `1`: fraudulent transaction

### Supervised-Learning Task

The supervised component is a binary classification problem. It will learn from transactions with known labels and estimate the probability that a new transaction is fraudulent.

The relationship can be represented as:

`Transaction features (X) → Fraud probability → Predicted class`

### Unsupervised-Learning Task

The unsupervised component will analyse transaction features without using fraud labels during training. It will assign an anomaly score representing how unusual each transaction appears compared with other transactions.

The relationship can be represented as:

`Transaction features (X) → Anomaly score`

Known fraud labels may subsequently be used to evaluate whether anomalous transactions correspond to actual fraud.

### Intended Model Output

The completed system should produce:

- A fraud probability from the supervised model
- An anomaly score from the unsupervised model
- A risk classification
- A recommendation to approve or investigate the transaction
- An explanation of the factors influencing high-risk predictions

### Prediction Setting

The project will simulate transaction-level fraud screening using historical data. In a real deployment, the trained system could score transactions close to the time at which they occur.


## 1.3 Project Scope

### Scope Definition

This project focuses on transaction-level fraud detection and anomaly detection for a fictional digital-payment company.

The system will analyse historical financial transactions and estimate the risk associated with each individual transaction. It will support fraud investigators by prioritising potentially suspicious transactions rather than making final legal or regulatory decisions.

### In Scope

The project will include:

- Understanding and exploring financial transaction data
- Detecting fraudulent transactions using supervised classification
- Detecting unusual transactions using unsupervised anomaly detection
- Assigning fraud probabilities and anomaly scores
- Investigating class imbalance
- Comparing sampling and class-weighting techniques
- Engineering behavioural and historical features when supported by the data
- Comparing several machine-learning algorithms
- Evaluating precision, recall, F1-score, ROC-AUC and PR-AUC
- Analysing false positives and false negatives
- Selecting decision thresholds using model performance and business costs
- Explaining model predictions
- Developing an interactive fraud-monitoring application
- Maintaining a reproducible project using Git and GitHub
- Exploring scalable processing as an optional extension

### Out of Scope

The initial project will not include:

- Integration with a real banking or payment-production system
- Real-time blocking of financial transactions
- Facial, fingerprint or other biometric recognition
- Cybersecurity network-intrusion detection
- Automatic closure of customer accounts
- Automatic submission of regulatory reports
- Use of identifiable or confidential customer information
- Cryptocurrency, insurance, loan-application or employee fraud
- Claims that an anomaly automatically proves criminal activity

### Intended Use

The model is intended as a decision-support tool. A high-risk prediction should trigger additional verification or investigation rather than automatically establish that fraud occurred.

### Dataset Limitations

The indicators that can be implemented will depend on the available dataset columns. Features such as device changes, account age, location anomalies and authentication failures can only be developed if the dataset contains the necessary information.

The project will not invent unavailable customer information. Any unavailable real-world indicators will be discussed as possible future improvements.

## 1.4 Success Criteria

### Definition of Success

The project will be considered successful if it produces a reproducible and explainable system that performs meaningfully better than a simple baseline model while balancing fraud detection against unnecessary alerts.

Because fraudulent transactions are expected to represent a small minority of the dataset, overall accuracy will not be treated as the primary measure of success. A model that predicts every transaction as legitimate could achieve high accuracy while detecting no fraud.

### Primary Evaluation Criteria

The main technical criteria will include:

- **Recall:** the proportion of actual fraudulent transactions detected
- **Precision:** the proportion of fraud alerts that correspond to actual fraud
- **F1-score:** a combined measure of precision and recall
- **PR-AUC:** performance across precision-recall trade-offs
- **False-positive volume:** the number of legitimate transactions incorrectly flagged
- **False negatives:** the number of fraudulent transactions missed
- **Alert volume:** the number of transactions requiring investigation
- **Estimated financial cost:** the combined impact of missed fraud and false alerts

### Operational Criteria

The system should:

- Produce understandable fraud probabilities or anomaly scores
- Support threshold selection based on investigation capacity
- Apply consistent data-processing steps
- Avoid data leakage
- Provide explanations for high-risk predictions
- Produce outputs that can be understood by fraud investigators

### Project-Quality Criteria

The repository should:

- Use a clear and reproducible folder structure
- Record meaningful development milestones with Git
- Include understandable documentation
- Separate exploratory notebooks from reusable Python code
- Include appropriate tests
- Provide instructions for running the final application

### Provisional Nature of Targets

Exact numerical targets will not be established before the dataset and baseline model have been examined.

After baseline evaluation, measurable targets will be selected using:

- The observed fraud rate
- Baseline model performance
- The cost of missed fraud
- The cost of false alerts
- The number of alerts investigators can review

The final model should improve meaningfully on the baseline without creating an operationally unmanageable number of alerts.

## 1.4 Success Criteria

### Definition of Success

The project will be considered successful if it produces a reproducible and explainable system that performs meaningfully better than a simple baseline model while balancing fraud detection against unnecessary alerts.

Because fraudulent transactions are expected to represent a small minority of the dataset, overall accuracy will not be treated as the primary measure of success. A model that predicts every transaction as legitimate could achieve high accuracy while detecting no fraud.

### Primary Evaluation Criteria

The main technical criteria will include:

- **Recall:** the proportion of actual fraudulent transactions detected
- **Precision:** the proportion of fraud alerts that correspond to actual fraud
- **F1-score:** a combined measure of precision and recall
- **PR-AUC:** performance across precision-recall trade-offs
- **False-positive volume:** the number of legitimate transactions incorrectly flagged
- **False negatives:** the number of fraudulent transactions missed
- **Alert volume:** the number of transactions requiring investigation
- **Estimated financial cost:** the combined impact of missed fraud and false alerts

### Operational Criteria

The system should:

- Produce understandable fraud probabilities or anomaly scores
- Support threshold selection based on investigation capacity
- Apply consistent data-processing steps
- Avoid data leakage
- Provide explanations for high-risk predictions
- Produce outputs that can be understood by fraud investigators

### Project-Quality Criteria

The repository should:

- Use a clear and reproducible folder structure
- Record meaningful development milestones with Git
- Include understandable documentation
- Separate exploratory notebooks from reusable Python code
- Include appropriate tests
- Provide instructions for running the final application

### Provisional Nature of Targets

Exact numerical targets will not be established before the dataset and baseline model have been examined.

After baseline evaluation, measurable targets will be selected using:

- The observed fraud rate
- Baseline model performance
- The cost of missed fraud
- The cost of false alerts
- The number of alerts investigators can review

The final model should improve meaningfully on the baseline without creating an operationally unmanageable number of alerts.


## 1.5 Dataset Selection

### Candidate Datasets

Three public datasets were considered:

1. The ULB Credit Card Fraud Detection dataset
2. The BankSim bank-payment simulation dataset
3. The PaySim mobile-money simulation dataset

The ULB dataset contains real anonymised transactions and is suitable for studying severe class imbalance. However, most features are anonymised, and the dataset does not provide customer identifiers required for customer-level historical analysis.

PaySim contains understandable sender, recipient, balance and transaction-type information. However, its size makes it better suited to a later large-data extension.

### Selected Primary Dataset

BankSim was selected as the primary dataset.

BankSim is a synthetic bank-payment dataset designed for fraud-detection research. It contains approximately 594,643 transactions, including approximately 7,200 fraudulent transactions.

It includes customer identifiers, merchant identifiers, transaction categories, transaction amounts, time steps and historical fraud labels.

### Reasons for Selection

BankSim was selected because:

- Its size is manageable on the available local computer.
- It contains interpretable features.
- It represents an imbalanced fraud-detection problem.
- Customer identifiers permit behavioural feature engineering.
- Time steps allow previous activity to be separated from future activity.
- Merchant and category variables support meaningful analysis.
- It contains labels for supervised learning.
- The labels can be withheld during unsupervised anomaly detection.
- It contains no directly identifiable real customer information.

### Planned Dataset Usage

The datasets will be used in the following order:

1. BankSim will support the main end-to-end project.
2. The ULB Credit Card Fraud dataset may provide a secondary benchmark.
3. PaySim may be used as an optional large-scale extension.

Additional datasets will only be introduced after the primary BankSim project is complete.

### Dataset Limitations

BankSim is synthetic and cannot perfectly represent every real financial institution.

It does not provide all signals used by real-world fraud systems, such as device fingerprints, login attempts, account creation dates, precise locations and investigator notes.

The project will only implement indicators supported by the available data and will clearly distinguish demonstrated capabilities from proposed future extensions.


## Phase 1 Progress

- [x] 1.1 Define the business problem
- [x] 1.2 Convert the business problem into a machine-learning problem
- [x] 1.3 Define the project scope
- [x] 1.4 Establish success criteria
- [x] 1.5 Compare and select datasets
- [ ] 1.6 Consider privacy, ethics and limitations