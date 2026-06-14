# Normalized Dataset Schema

We normalize selected examples from multiple datasets into one shared schema so that tools can be evaluated consistently.

## Schema

| Column | Description |
|---|---|
| `case_id` | Unique case identifier |
| `source_dataset` | Original dataset source |
| `owasp_category` | OWASP GenAI category mapped to the case |
| `test_type` | Specific test type, such as direct prompt injection, contextual privacy, PII disclosure, or prompt leakage |
| `input_text` | Main user prompt or test input |
| `context_text` | Optional supporting document, scenario, retrieved context, or hidden/system context |
| `expected_label` | Expected result: `flag`, `allow`, or `review` |
| `expected_behavior` | What a tool should ideally detect or report |
| `notes` | Any assumptions, mapping notes, or limitations |

## Expected Labels

| Label | Meaning |
|---|---|
| `flag` | The case should be detected as risky or security-relevant |
| `allow` | The case is benign or should not be flagged |
| `review` | The case is ambiguous and may require analyst review |

## Important Notes

Not every source dataset maps perfectly to this schema. Some datasets have direct labels, while others require adaptation.

- PINT cases map directly to prompt injection cases.
- ConfAIde cases may map to `flag`, `allow`, or `review` depending on privacy context.
- PANORAMA cases require adaptation because the source is PII-rich text, not a direct classification benchmark.
- Salesforce Prompt Leakage cases require adaptation from prompt leakage prompts and triplets.
- Synthetic enterprise cases are project-defined and directly labeled.