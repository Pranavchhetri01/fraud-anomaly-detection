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

## Phase 1 Progress

- [x] 1.1 Define the business problem
- [ ] 1.2 Convert the business problem into a machine-learning problem
- [ ] 1.3 Define the project scope
- [ ] 1.4 Establish success criteria
- [ ] 1.5 Compare and select datasets
- [ ] 1.6 Consider privacy, ethics and limitations