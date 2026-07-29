# Signal Rules V1

Version: 1.0

## Purpose

Score current timing evidence from 0 to 100 independently of ICP fit. A high signal score cannot repair poor structural fit.

## Signal library

- funding;
- hiring;
- growth;
- acquisitions;
- leadership changes;
- new markets;
- product launches;
- events;
- company news;
- job postings;
- promotions;
- public posts;
- technology-stack changes.

## Scoring dimensions

Each dimension answers a different question.

### Relevance — 25

How directly does the event imply a need for CRM, revenue operations, sales process, automation, data quality, or GTM infrastructure?

### Personalisation value — 20

Does the evidence enable a specific, useful outreach angle tied to the company's situation rather than a generic message?

### Strength — 20

Is this a material business event or merely a weak indicator?

### Freshness — 15

- 15: within 30 days
- 12: 31–90 days
- 8: 91–180 days
- 4: 181–365 days
- 0: older than one year or undated

### Reliability — 10

- 10: official company source, filing, or direct leadership statement
- 8: reputable publication or verified platform
- 5: credible secondary source
- 2: weak or unverified source
- 0: unsupported inference

### Clustering — 10

- 10: three or more mutually reinforcing current signals
- 6: two reinforcing signals
- 2: one signal with a minor supporting indicator
- 0: isolated signal

Clustering is an uplift, not a requirement. A single strong, fresh and reliable signal can still score well.

## Primary signal

Return the most relevant current signal in one concise sentence with its date or timeframe. If no meaningful current signal is found, return exactly:

`No meaningful current signal found.`

## Missing and conflicting evidence

- Do not manufacture recency.
- Do not count duplicated reporting as multiple signals.
- Distinguish a company event from third-party speculation.
- Lower reliability and confidence when the original source cannot be confirmed.
- If signal dates conflict, use the most authoritative dated source and disclose the conflict.
