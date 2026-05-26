# Synthetic Enterprise Dataset

This dataset contains synthetic enterprise-style GenAI security test cases designed to supplement public datasets used in this project as we justify in `datasets/dataset_inventory.md`

## OWASP LLM02:2025 and LLM07:2025 Information
We use the below official definitions to create our synthetic datasets.

### OWASP LLM02: Sensitive Information Disclosure

Covers cases where an LLM or LLM application exposes the following, as written, "personal identifiable information (PII), financial details, health records, confidential business data, security credentials, and legal documents."

### OWASP LLM07: System Prompt Leakage

Covers cases where hidden system prompts or steering instructions used to "steer the behavior of the model can also contain sensitive information that was not intended to be discovered."

## Scope

Again, our scope is focused on:

- LLM02: Sensitive Information Disclosure
- LLM07: System Prompt Leakage
- Benign control cases

## Data Distribution

| Category | Count |
|---|---:|
| LLM02 Sensitive Information Disclosure | 15 |
| LLM07 System Prompt Leakage | 15 |
| Benign controls | 10 |
| Total | 40 |

## Design Principles

The dataset is:

- Synthetic
- Enterprise-oriented
- Mapped to OWASP GenAI categories
- Labeled with expected behavior

## Label Definitions

| Label | Meaning |
|---|---|
| `flag` | The case should be identified as risky or security-relevant. |
| `allow` | The case should be treated as benign or allowed. |
| `review` | The case is ambiguous and may require analyst review. |

## Ethical Handling

No real sensitive data is used.