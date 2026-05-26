# Dataset Inventory

This inventory documents the datasets considered, their formats, labeling structure, OWASP GenAI mapping, and intended MVP use.

| Dataset | OWASP Category | Purpose | Format | Labels | MVP Use | Notes |
|---|---|---|---|---|---|---|
| Lakera PINT | LLM01 Prompt Injection | Prompt injection detection benchmark | YAML / DataFrame-style records | Yes. Binary label plus category | Yes | PINT expects records with `text`, `category`, and `label`. The dataset is designed for prompt injection detection and includes 4,314 total inputs, including English and non-English inputs. |
| ConfAIde | LLM02 Sensitive Information Disclosure | Contextual privacy and sensitive disclosure reasoning | CSV + JSON evaluation outputs | Yes. Privacy ratings, preference annotations, and eval results | Yes | ConfAIde uses contextual integrity theory and includes benchmark tiers with scenario, information, generic/revealing answers, human preference labels, and model evaluation results. Labels are not always simple binary classes, but they are useful for privacy reasoning. |
| PANORAMA | LLM02 Sensitive Information Disclosure | Synthetic PII-rich text for privacy and sensitive-data testing | Parquet via Hugging Face | Partially. Synthetic profile attributes, content-type metadata, and PII-rich fields | Yes | PANORAMA contains synthetic profiles and PII-rich natural text across content types such as biographies, social posts, forums, reviews, comments, and marketplace listings. It is not a simple supervised classification dataset, so we will sample and adapt records into sensitive disclosure test cases. |
| Salesforce Prompt Leakage | LLM07 System Prompt Leakage | Prompt leakage and multi-turn system prompt extraction benchmark | JSON triplets + CSV fine-tuning data | Partiall. Triplets are unlabeled; fine-tuning CSV includes `type` categories | Yes | Public datasets are organized across news, legal, finance, and medical domains. Triplet JSON files contain `query`, `doc1`, and `doc2`; the fine-tuning CSV has `id`, `prompt`, and `type`. We will use these for prompt leakage test scenarios. |
| Synthetic Enterprise Set | LLM02 / LLM07 | Security-function relevance and enterprise-style examples | CSV | Yes. Project-defined labels | Yes | Synthetic cases will include fake API keys, fake employee records, fake incident summaries, fake access tokens, and honeytoken-based system prompt leakage examples. No real sensitive data is used. |

## Dataset Selection Rationale

We use a mixed dataset strategy. Public datasets are used where available, while synthetic enterprise examples are added where public datasets do not fully match the intended security-function use case.

- Lakera PINT provides a public benchmark for LLM01 Prompt Injection.
- ConfAIde and PANORAMA support LLM02 Sensitive Information Disclosure from two angles: contextual privacy reasoning and synthetic PII-rich text.
- Salesforce Prompt Leakage supports LLM07 System Prompt Leakage and multi-turn prompt extraction scenarios.

We also create and use a **Synthetic Enterprise Set** to address gaps not fully covered by the public datasets:

- Lakera PINT focuses on prompt injection, not sensitive enterprise security records.
- ConfAIde supports privacy reasoning, but is not centered on SOC, IR, or AppSec workflows.
- PANORAMA contains PII-rich synthetic text, but is not formatted as tool-evaluation prompts.
- Salesforce Prompt Leakage focuses on prompt leakage, but is not specifically oriented around enterprise security functions.

## Labeling Notes

Not all datasets use the same label structure.

- Lakera PINT has a direct binary/category labeling structure.
- ConfAIde includes privacy, preference, and evaluation annotations rather than one simple label.
- PANORAMA contains synthetic PII/profile metadata and must be adapted into test cases.
- Salesforce Prompt Leakage includes unlabeled triplet JSON files and a fine-tuning CSV with leakage prompt `type` categories.
- Synthetic examples will use project-defined labels such as `flag`, `allow`, and `review`.

## MVP Dataset Plan

For the MVP, we will create a normalized dataset with a shared schema:

```csv
case_id,source_dataset,owasp_category,test_type,input_text,context_text,expected_label,expected_behavior,notes
```