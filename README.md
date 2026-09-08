---
license: cc-by-4.0
pretty_name: "SafeLegalAI Legal Tech Tools — governance facts"
language:
  - en
multilinguality:
  - monolingual
annotations_creators:
  - expert-generated
language_creators:
  - found
source_datasets:
  - original
size_categories:
  - n<1K
tags:
  - legal
  - legaltech
  - ai-governance
  - vendor-due-diligence
  - data-protection
  - security
  - generative-ai
  - law
  - courts
  - ai-regulation
  - ai-safety
  - safelegalai
configs:
  - config_name: tools
    default: true
    data_files:
      - split: train
        path: data/tools.jsonl
---

# SafeLegalAI Legal Tech Tools — governance facts

**What does each legal tech tool actually document about training, retention, certification, residency and accuracy?**

128 tools · 78 publish a no-training commitment · 15 categories · last checked 2026-09-04 · synced from [safelegalai.com](https://safelegalai.com) on 2026-09-08.

Governance facts per legal tech product — disclosed model providers, SOC 2 / ISO 27001 / ISO 42001, data residency, no-training and zero-retention commitments, private deployment, DPA, trust and sub-processor pages, published accuracy evidence (vendor or third-party), and incidents on the record — each fact linked to the vendor page that states it. `unknown` means unknown: fields are never guessed. This is a facts registry, never a ranking.

This is a mirror. The canonical, always-current version lives at **[safelegalai.com/tools](https://safelegalai.com/tools)**, where every record has a permanent page, a citation block and its last-checked date; the JSON served there ([/tools/tools.json](https://safelegalai.com/tools/tools.json)) is the source of this repository. Each row's `url` field points to its record page. The same files are mirrored on GitHub at [github.com/SafeLegalAI/legal-ai-tools](https://github.com/SafeLegalAI/legal-ai-tools) (issues welcome there).

## Tables

| config | rows | what a row is | files |
|---|---|---|---|
| `tools` | 129 | one row per product | [`data/tools.jsonl`](data/tools.jsonl) · [`csv/tools.csv`](csv/tools.csv) |

## Fields

| field | meaning |
|---|---|
| `name` · `vendor` · `website` · `hq` · `founded` · `category` · `subcategories` · `description` | the product |
| `targetUsers` · `models` · `markets` | who it is for, which model providers are disclosed, which markets it serves |
| `pricing` | `{model, public, url}` |
| `security` | `{soc2, iso27001, iso42001, dataResidency[], noTrainingOnCustomerData, zeroRetention, privateDeployment, dpa, trustUrl, subprocessorsUrl, privacyUrl, termsUrl}` — yes · no · unknown |
| `accuracyEvidence` | `[{label, url, by: vendor|third-party, note}]` |
| `incidents` · `relatedIncidents` | court incidents, lawsuits or regulator attention naming the tool; slugs into the incident dataset |
| `ownership` · `ownershipNote` | `own-product` marks LegalAI Space, built by the same team; it is labelled, never scored, ranked, compared or counted (see disclosure below) |
| `status` · `verified` · `sources` · `lastVerified` | active · acquired · shut-down · beta; provenance and check date |

Dates are `YYYY-MM-DD`. Optional fields are absent (JSONL) or empty (CSV) when unknown — nothing is guessed. In the CSV, arrays of scalars are joined with `; ` and nested objects are JSON strings.

## Method

We record findings made by courts and regulators; we do not make them. Every record links a primary source (judgment, order, regulator notice, official document or vendor page) and carries the date it was last re-opened against that source. Unverified records are flagged `unverified`, never silently included. Inclusion criteria, the correction process and the ownership/funding disclosure are published at [safelegalai.com/editorial-standards](https://safelegalai.com/editorial-standards); every content run is logged at [safelegalai.com/changelog](https://safelegalai.com/changelog).

**Disclosure.** One record (`ownership: own-product`) is LegalAI Space, a Cognesio LLP product. It is listed with a permanent ownership label and only the facts it publishes; it is never scored, ranked, reviewed, compared or counted in any aggregate statistic, and is excluded from the counts above. Full policy: https://safelegalai.com/about.

## Use

```python
from datasets import load_dataset
ds = load_dataset("safelegalaidata/legal-ai-tools")
```

## Uses

**Suited to:** counting and comparing what the record shows (by court, jurisdiction, date, actor, outcome, status); building watch-lists and alerts from the `url` and last-checked fields; grounding retrieval or summarisation on cited primary documents; teaching and library guides that need a dated, sourced list.

**Not suited to:** ranking products, people or courts; inferring prevalence beyond what a court or regulator has itself stated; any use that treats a coding column as a finding of fact or law. Where a row names a person or organisation it does so as they appear in a public document; anyone named may request a correction or right of reply at https://safelegalai.com/report.

## Cite

> SafeLegalAI (published by Cognesio LLP), "Legal Tech Tools — governance facts", safelegalai.com, accessed 2026-09-08. https://safelegalai.com/tools — data: CC BY 4.0.

```bibtex
@dataset{safelegalai_legal_ai_tools_2026_09_08,
  title        = {Legal Tech Tools — governance facts},
  author       = {{SafeLegalAI (Cognesio LLP)}},
  year         = {2026},
  url          = {https://safelegalai.com/tools},
  note         = {Mirror: https://huggingface.co/datasets/safelegalaidata/legal-ai-tools. Data CC BY 4.0. Last checked 2026-09-04.}
}
```

Cite the primary source as the authority and this dataset as the structured record that surfaced it. Corrections and right of reply: [safelegalai.com/report](https://safelegalai.com/report).

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribution: **SafeLegalAI (safelegalai.com), published by Cognesio LLP** with a link to https://safelegalai.com/tools. Primary sources keep their own licences and copyright.

## Disclaimer and notices

**Provided "as is", without warranty of any kind** — the CC BY 4.0 licence excludes all warranties and limits liability (section 5), and those exclusions apply to this dataset. **Not legal advice**; no lawyer–client relationship arises from using it. Cognesio LLP is not a law firm. SafeLegalAI records findings made by courts, regulators and vendors' own published pages; it makes no findings of its own, and the linked official documents are the record. Editorial classifications (status labels, requirement codes, "documented yes/no/not disclosed") are opinions about documents, expressed in good faith; the document prevails. Where a row names a person or organisation, it does so as they appear in a public court document, official publication or their own published material — a fair and accurate report published in good faith and in the public interest; anyone named may reply or request a correction at https://safelegalai.com/report. Product, company, court and regulator names and marks belong to their owners and identify the product or body referred to; no affiliation or endorsement is implied. Full terms and notice-and-takedown: https://safelegalai.com/disclaimer.

## Related datasets

- [Legal AI Incident Tracker](https://huggingface.co/datasets/safelegalaidata/legal-ai-incidents) — canonical page https://safelegalai.com/tracker
- [Legal AI Regulation Map](https://huggingface.co/datasets/safelegalaidata/legal-ai-regulation-map) — canonical page https://safelegalai.com/regulation
- [Legal AI Regulation Documents (versioned)](https://huggingface.co/datasets/safelegalaidata/legal-ai-regulation-documents) — canonical page https://safelegalai.com/regulation/documents
- [All datasets and what is in preparation](https://safelegalai.com/datasets)

## Manifest

```json
{
  "dataset": "SafeLegalAI Legal Tech Tools — governance facts",
  "canonical": "https://safelegalai.com/tools",
  "source": "https://safelegalai.com/tools/tools.json",
  "catalogue": "https://safelegalai.com/datasets",
  "publisher": "Cognesio LLP",
  "license": "CC BY 4.0",
  "licenseUrl": "https://creativecommons.org/licenses/by/4.0/",
  "lastChecked": "2026-09-04",
  "synced": "2026-09-08",
  "notice": "Provided as is, without warranty; not legal advice. SafeLegalAI records findings made by courts, regulators and vendors' own pages; the linked official documents are the record. Names and marks belong to their owners. Terms: https://safelegalai.com/disclaimer",
  "tables": {
    "tools": 129
  },
  "contentSha256": "adb7fa8cff3687214033073b59b59d83beb11b620fd5c0da10dc8b0927249fa3"
}
```
