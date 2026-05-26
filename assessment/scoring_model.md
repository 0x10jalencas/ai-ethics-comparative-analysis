# Scoring Model

We use a lightweight MCDA-informed scoring model to compare GenAI security tools. We also explain why each "dimension" has been assigned its respective weight. Below is an explanation to the MCDA model we use, with context.

Organizations often have diverse priorities and conflicting interests. Organizations also often evalaute tools across multiple competing criteria. This is known as the “n > 2 criteria” problem when more than two criteria are important and there may be no single option that is objectively best across all dimensions. MCDA-style methods can help make these trade-offs explicit by (1) defining criteria, (2) assigning weights, (3) scoring alternatives, and (4) applying a transparent decision rule.

We use swing weighting as a lightweight way to assign relative importance to each criterion. The method is based on the following thought experiment: **Imagine a baseline scenario where all criteria are at their worst possible state (a score of zero). If you could upgrade only a limited number of these criteria to their best possible performance, which ones would deliver the highest strategic value? Your choices inform  how the model's weights are assigned. These choices are often defined by organizations in accordance with their adherence to relevant frameworks (i.e. industry frameworks), stakeholder priorities, security functions, etc.**

## Compensatory and Non-Compensatory Logic
We use a hybrid MCDA-informed, employing both non-compensatory and compensatory features described below.

“Gate criteria” are non-compensatory. For example, a tool cannot compensate for failing ethical testability or having no relevance to the selected OWASP GenAI categories. Even if the tool scores highly in one area, it should not be recommended for AI adoption under this project scope if it fails a required gate.

Tools that pass the gate criteria then move into the compensatory part of the model: the weighted scorecard. In this stage, high performance in one category can offset weaker performance in another. This kind of approach is useful because tool evaluation often involves explicit trade-offs. For example, a red-team-focused group may prioritize strong evaluation capability and multi-turn testing, even if the tool has more limited governance or reporting features.


## Criteria

| Dimension | Weight |
|---|---:|
| Risk Coverage | 20 |
| Evaluation Capability | 25 |
| Measurement and Evidence Quality | 20 |
| Operational Fit | 20 |
| Governance and Adoption Readiness | 15 |
| Total | 100 |

## 1. Risk Coverage - 20 points

Measures whether the tool addresses the selected OWASP GenAI categories.

Subcriteria:
- LLM01 Prompt Injection support
- LLM02 Sensitive Information Disclosure support
- LLM07 System Prompt Leakage support
- Ability to map findings to OWASP/NIST categories

## 2. Evaluation Capability — 25 points

Measures whether the tool can actually run useful assessments.

Subcriteria:
- Dataset compatibility
- Attack/test depth
- Multi-turn support
- Target flexibility
- Safe testing with public/synthetic data

## 3. Measurement and Evidence Quality — 20 points

Measures whether outputs are useful as assessment evidence.

Subcriteria:
- Repeatable execution
- Quantitative or structured results
- False-positive/false-negative analysis possible
- Exportable artifacts
- Clear limitations

## 4. Operational Fit — 20 points

Measures whether the tool could fit security workflows.

Subcriteria:
- CLI/API/scriptability
- CI/CD fit
- SOC/SIEM export potential
- Issue-tracker or reporting workflow fit
- Setup and maintenance burden

## 5. Governance and Adoption Readiness — 15 points

Measures whether the tool supports responsible adoption.

Subcriteria:
- Auditability and traceability
- Documentation quality
- Role fit for security functions
- Training/skill requirements identifiable
- Support for risk communication

## Limitations

This scoring model is intended for comparative analysis under the project scope. As it stands, there is no universal ranking of GenAI security tools.