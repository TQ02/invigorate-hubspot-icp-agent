# ICP Rules V1

Version: 1.0

## Purpose

Score structural company fit from 0 to 100. This score must not include current buying signals. Missing facts receive no positive points and reduce research confidence; they do not automatically make a company poor fit.

## Evidence hierarchy

Prefer, in order:

1. the company's current official website and official filings;
2. recent official company profiles, hiring pages and leadership material;
3. reputable business databases and publications;
4. credible third-party profiles;
5. inference, clearly labelled and used only when direct evidence is unavailable.

When sources conflict, prefer the newest authoritative source, describe the conflict, and lower confidence.

## Scoring

### 1. B2B model and offer relevance — 20

| Points | Rule |
|---:|---|
| 20 | Clear B2B offer with a sales-led, consultative or recurring-revenue motion that benefits from CRM and GTM systems. |
| 14 | Primarily B2B, but sales complexity or fit is only partially evidenced. |
| 7 | Mixed B2B/B2C or indirect relevance. |
| 0 | Primarily consumer, public-only, non-commercial, or clearly irrelevant. |

### 2. Annual revenue fit — 20

| Points | Rule |
|---:|---|
| 20 | Approximately €1m–€2m. |
| 17 | Approximately €2m–€5m. |
| 12 | Approximately €500k–€999k or €5m–€10m. |
| 6 | Below €500k or €10m–€25m. |
| 2 | Above €25m. |
| 0 | No usable evidence. |

Do not substitute employee count for revenue. A clearly labelled estimate is acceptable only when its basis is stated.

### 3. Employee count fit — 15

| Points | Rule |
|---:|---|
| 15 | Approximately 20–50 employees. |
| 13 | Approximately 51–100 employees. |
| 9 | Approximately 10–19 or 101–200 employees. |
| 4 | Fewer than 10 or 201–500 employees. |
| 1 | More than 500 employees. |
| 0 | No usable evidence. |

### 4. Sales-team size fit — 15

| Points | Rule |
|---:|---|
| 15 | Approximately 4–10 sales or business-development staff. |
| 11 | Approximately 2–3 or 11–15. |
| 6 | One or 16–25. |
| 2 | None evident or more than 25. |
| 0 | No usable evidence. |

Use current leadership and employee evidence. Do not infer a precise sales-team size from total headcount alone.

### 5. CRM and GTM infrastructure need — 20

| Points | Rule |
|---:|---|
| 20 | Clear operational complexity, scaling pressure, fragmented process, multi-stage selling, or evidence of CRM/GTM improvement need. |
| 14 | Plausible need supported by two or more operational indicators. |
| 7 | General fit but weak evidence of current need. |
| 0 | Mature in-house capability, very simple motion, or no usable evidence. |

### 6. Geography and decision environment — 10

| Points | Rule |
|---:|---|
| 10 | Ireland, UK, or another serviceable market with identifiable local decision-makers and compatible operating context. |
| 7 | Serviceable European or English-speaking market with reasonable access. |
| 3 | Serviceable but materially harder decision environment. |
| 0 | Outside serviceable scope or no usable evidence. |

## Classification

- Ideal: 85–100
- Strong: 70–84
- Possible: 50–69
- Weak: 30–49
- Poor: 0–29

## Missing and conflicting data

- Never invent a value.
- Name the missing criterion in the reasoning.
- Score only supported evidence.
- Lower confidence when revenue, employee count, sales-team size, or core business model is missing.
- If evidence materially conflicts, state both positions, use the most defensible current value, and lower confidence.
- Keep the output deterministic: the classification must match the numeric score band.
